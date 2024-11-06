![image](https://github.com/user-attachments/assets/a5ca1df2-cb3e-41bf-8dc8-6482f01f60bc)
![image](https://github.com/user-attachments/assets/11e4ae41-6174-4560-a9ef-363fb21e1275)
![image](https://github.com/user-attachments/assets/8e9f38dc-28d2-4e0c-b760-83329c201edd)
![image](https://github.com/user-attachments/assets/a81660b2-0d77-4b32-9ae8-9983d56ca554)
![image](https://github.com/user-attachments/assets/5d1ce2ea-c30b-40e7-ba57-1854f2f85368)
![image](https://github.com/user-attachments/assets/ab76a6d7-a580-47b2-8cb1-b94d79344716)
![image](https://github.com/user-attachments/assets/8a9b0b66-1fe4-458d-bb0f-1104f22f27c4)
![image](https://github.com/user-attachments/assets/f4f6b22a-36c1-46f1-8c7e-c2d97aa0c92f)
![image](https://github.com/user-attachments/assets/da0df2c7-0c98-40eb-81f7-2350f30ebc0f)
![image](https://github.com/user-attachments/assets/9bffe62a-ab34-46a9-9e8e-9a0e41d673a6)
![image](https://github.com/user-attachments/assets/fb0fba0c-2924-48d0-ba94-18a3c10bc10b)
![image](https://github.com/user-attachments/assets/d7e3e84c-79ee-405e-8fba-791b295e54d4)
```
import subprocess

def list_git_objects():
    objects = subprocess.check_output(['git', 'rev-list', '--objects', '--all']).decode().splitlines()
    
    for line in objects:
        sha1, *path = line.split()
        
        print(f"Object SHA-1: {sha1}")
        
        try:
            content = subprocess.check_output(['git', 'cat-file', '-p', sha1]).decode()
            print(f"Contents of {sha1} ({' '.join(path) if path else 'no path'}):")
            print(content)
            print("-" * 40)
        except subprocess.CalledProcessError as e:
            print(f"Error reading object {sha1}: {e}")
            continue

list_git_objects()
```
![image](https://github.com/user-attachments/assets/80c55751-ec8e-4449-b682-64a606cfcaf0)



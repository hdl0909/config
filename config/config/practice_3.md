![image](https://github.com/user-attachments/assets/5d77cfd0-568c-4980-a114-8f7d8718c896)

**КОД:**
```
local groups = ["ИКБО-" + x + "-20" for x in std.range(1, 25)];
local createStudent(age, group, name) = {
   age: age,
   group: group,
   name: name
};
local students = 
[
createStudent(19, "ИКБО-4-20", "Иванов И.И."),
createStudent(18, "ИКБО-5-20", "Петров П.П."),
createStudent(18, "ИКБО-5-20", "Сидоров С.С."),
createStudent(19, "ИКБО-1-20", "Хайруллин Д.Л.")];
{
  groups: groups,
  students: students,
  subject: "Конфигурационное управление"
}

```
![image](https://github.com/user-attachments/assets/594062a5-5c53-4f3b-ac18-f5194ee08005)
![image](https://github.com/user-attachments/assets/0c237bcb-2f73-4924-bea3-b4939adab321)
![image](https://github.com/user-attachments/assets/db12726f-c0bb-49ec-ad3b-a2ff2107d0b0)
![image](https://github.com/user-attachments/assets/ae6011dc-cc93-4e95-8c6d-94b349cb7060)
```
{
  "groups": [
    "ИКБО-1-20",
    "ИКБО-2-20",
    "ИКБО-3-20",
    "ИКБО-4-20",
    "ИКБО-5-20",
    "ИКБО-6-20",
    "ИКБО-7-20",
    "ИКБО-8-20",
    "ИКБО-9-20",
    "ИКБО-10-20",
    "ИКБО-11-20",
    "ИКБО-12-20",
    "ИКБО-13-20",
    "ИКБО-14-20",
    "ИКБО-15-20",
    "ИКБО-16-20",
    "ИКБО-17-20",
    "ИКБО-18-20",
    "ИКБО-19-20",
    "ИКБО-20-20",
    "ИКБО-21-20",
    "ИКБО-22-20",
    "ИКБО-23-20",
    "ИКБО-24-20"
  ],
  "students": [
    {
      "age": 19,
      "group": "ИКБО-4-20",
      "name": "Иванов И.И."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Петров П.П."
    },
    {
      "age": 18,
      "group": "ИКБО-5-20",
      "name": "Сидоров С.С."
    },
    <добавьте ваши данные в качестве четвертого студента>
  ],
  "subject": "Конфигурационное управление"
}
```
**КОД:**
```
let List/map = https://prelude.dhall-lang.org/List/map
let List/generate = https://prelude.dhall-lang.org/v15.0.0/List/generate

let groups = List/generate 24 Text (\(n : Natural) -> "ИКБО-${Natural/show (n + 1)}-20")

let Student = {age: Natural, group: Text, name: Text}

let students : List Student = 
[ { age = 19, group = "ИКБО-4-20", name = "Иванов И.И." }, 
  { age = 18, group = "ИКБО-5-20", name = "Петров П.П." },
  { age = 18, group = "ИКБО-5-20", name = "Сидоров С.С." },
  { age = 19, group = "ИКБО-10-23", name = "Хайруллин Д.Л." }
]

let subject : Text = "Конфигурационное управление"

in {groups = groups, students = students, subject = subject}
```
![image](https://github.com/user-attachments/assets/478e7fe6-cc8c-46d3-aaae-48f0eca0ca02)
![image](https://github.com/user-attachments/assets/f6ab0e90-50f0-4aaa-98cd-f11912034321)
![image](https://github.com/user-attachments/assets/e33617b7-e3ad-4896-b814-e850c3c574b8)
![image](https://github.com/user-attachments/assets/7bcd6737-349d-4272-8ecd-14bba86e2147)
```
import random


def parse_bnf(text):
    '''
    Преобразовать текстовую запись БНФ в словарь.
    '''
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar


def generate_phrase(grammar, start):
    '''
    Сгенерировать случайную фразу.
    '''
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join([generate_phrase(grammar, name) for name in seq])
    return str(start)


BNF = '''
E = 0 | 1 | E 0 | E 1
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))
```
![image](https://github.com/user-attachments/assets/784eaaff-9be3-4f88-a7de-4b43b77c31dc)
![image](https://github.com/user-attachments/assets/4c79b4f9-d351-4ee4-86da-6855b433ddf5)

**КОД:**
```
import random


def parse_bnf(text):
    '''
    Преобразовать текстовую запись БНФ в словарь.
    '''
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar


def generate_phrase(grammar, start):
    '''
    Сгенерировать случайную фразу.
    '''
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join([generate_phrase(grammar, name) for name in seq])
    return str(start)


BNF = '''
E =  ( E ) | { E } | 
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))
```
![image](https://github.com/user-attachments/assets/da30dd8d-f84d-46c8-9284-eb6083d96e1f)
![image](https://github.com/user-attachments/assets/e0bcd784-f940-4104-879b-602e3ffc9170)
```
import random


def parse_bnf(text):
    '''
    Преобразовать текстовую запись БНФ в словарь.
    '''
    grammar = {}
    rules = [line.split('=') for line in text.strip().split('\n')]
    for name, body in rules:
        grammar[name.strip()] = [alt.split() for alt in body.split('|')]
    return grammar


def generate_phrase(grammar, start):
    '''
    Сгенерировать случайную фразу.
    '''
    if start in grammar:
        seq = random.choice(grammar[start])
        return ''.join([generate_phrase(grammar, name) for name in seq])
    return start


BNF = '''
E = T | E l T
T = F | T & F
F = x | y | ~ F | ( F )
'''

for i in range(10):
    print(generate_phrase(parse_bnf(BNF), 'E'))
```
![image](https://github.com/user-attachments/assets/e06b6f61-ff4f-4d73-90eb-d23cbde2b107)

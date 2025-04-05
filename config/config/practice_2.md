![image](https://github.com/user-attachments/assets/ef4fd90f-cda1-4042-886b-506d27d6272a)
```
pip install matplotlib
pip show matplotlib
```
![image](https://github.com/user-attachments/assets/ac2e3708-040c-4620-a450-a0c2609ef51f)
![image](https://github.com/user-attachments/assets/50d4938f-c139-4c7f-b8b0-f1c3cd19270c)
![image](https://github.com/user-attachments/assets/d7f8d742-db10-42a5-82bb-a1a98cb2da93)
![image](https://github.com/user-attachments/assets/efe3b5d4-ceb1-4859-adbc-e1a900c02adc)
```
npm info express
git clone https://github.com/expressjs/express.git
```
![image](https://github.com/user-attachments/assets/11740eec-0033-467a-81af-6904d2745e51)
![image](https://github.com/user-attachments/assets/6abf8d9c-83d4-47a5-9f3c-6884947c7db4)
![image](https://github.com/user-attachments/assets/ea2cf881-c2f4-449c-860d-a10ccbfa82de)
**Команда:**
```
echo 'digraph G {
  node [shape=box];
  matplotlib -> numpy;
  matplotlib -> pillow;
  matplotlib -> cycler;
}' > matplotlib.dot

echo 'digraph G {
  node [shape=box];
  express -> accepts;
  express -> array_flatten;
  express -> content_type;
}' > express.dot

dot -Tpng matplotlib.dot -o matplotlib.png
dot -Tpng express.dot -o express.png

fim matplotlib.png
fim express.png
```
![image](https://github.com/user-attachments/assets/a17bda2e-b798-4198-9e99-b995468397c2)
![image](https://github.com/user-attachments/assets/2a1dae6b-5b38-4eff-add1-41b08ac05fc0)
![image](https://github.com/user-attachments/assets/b8fb4e46-c73c-45f4-a063-308544de036e)
**КОД:**
```
include "globals.mzn";
array[1..6] of var 0..9: tickets;
constraint all_different(tickets);
constraint sum(tickets[1..3]) = sum(tickets[4..6]);
var int: sum_three_digits = sum(tickets[1..3]);
solve minimize sum_three_digits;

output ["Ticket: ", show(tickets)];
output [" Sum of first three digits: ", show(sum_three_digits)];
```
![image](https://github.com/user-attachments/assets/aaf34259-26a6-477d-b67d-a8381d526e3a)
![image](https://github.com/user-attachments/assets/e218ca8b-e359-4e7d-a443-8852d464a378)
**КОД:**
```
set of int: MenuVersion = {100, 110, 120, 130, 140, 150};
set of int: DropDownVersion = {180, 200, 210, 220, 230};
set of int: IconsVersion = {100, 200};

var MenuVersion: menu;
var DropDownVersion: dropdown;
var IconsVersion: icons;

% Ограничение для зависимости между menu и dropdown
constraint
  if menu >= 110 then
    dropdown >= 200
  else
    dropdown = 180
  endif;

% Ограничение для зависимости между dropdown и icons
constraint
  if dropdown >= 200 then
    icons = 200
  else
    icons = 100
  endif;
 
 output ["Menu Version: ", show(menu),
         "\nDropdown Version: ", show(dropdown),
         "\nIcons Versions: ", show(icons)]
```
![image](https://github.com/user-attachments/assets/9953aede-6742-4c32-8efe-9e96ea10a41c)
![image](https://github.com/user-attachments/assets/67263fe5-9078-47d4-b039-c0b8219625d3)
**КОД:**
```
int: root = 100;
var 100..300: foo;
var 100..300: target;
var 100..300: left;
var 100..300: right;
var 100..300: shared;

constraint
  root = 100 ->
  (foo >= 100 /\ foo < 200 /\ 
  target >= 200 /\ target < 300);
 
constraint
  foo = 110 -> 
  (left >= 100 /\ left < 200 /\
  right >= 100 /\ right < 200);
 
constraint
  (left = 100 -> shared >= 100) /\
  (right = 100 -> shared < 200);

constraint
  left = 100 ->
  (shared >= 100);
 
constraint
  right = 100 ->
  (shared < 200);
  
constraint
  shared = 100 ->
  (target >= 100 /\ target < 200);

output [
    "Root Version: ", show(root), "\n",
    "Foo Version: ", show(foo), "\n",
    "Left Version: ", show(left), "\n",
    "Right Version: ", show(right), "\n",
    "Shared Version: ", show(shared), "\n",
    "Target Version: ", show(target), "\n"
];
```
![image](https://github.com/user-attachments/assets/400defad-29cb-4ef3-aec3-d6dd2a3597a1)
![image](https://github.com/user-attachments/assets/78b9a605-f955-4547-89a6-e8f4280c031e)
**КОД:**
```
packages = {
    'root': {
        '1.0.0': {
            'dependencies': {
                'foo': '^1.0.0',
                'target': '^2.0.0'
            }
        }
    },
    'foo': {
        '1.1.0': {
            'dependencies': {
                'left': '^1.0.0',
                'right': '^1.0.0'
            }
        },
        '1.0.0': {
            'dependencies': {}
        }
    },
    'left': {
        '1.0.0': {
            'dependencies': {
                'shared': '>=1.0.0'
            }
        }
    },
    'right': {
        '1.0.0': {
            'dependencies': {
                'shared': '<2.0.0'
            }
        }
    },
    'shared': {
        '2.0.0': {
            'dependencies': {}
        },
        '1.0.0': {
            'dependencies': {
                'target': '^1.0.0'
            }
        }
    },
    'target': {
        '2.0.0': {
            'dependencies': {}
        },
        '1.0.0': {
            'dependencies': {}
        }
    }
}

def find_compatible_version(package_name, version_constraint, resolved):
    def is_compatible(version, min_version='', max_version=''):
        return (not min_version or version >= min_version) and (not max_version or version <= max_version)

    min_version, max_version = '', ''
    if version_constraint.startswith('^'):
        min_version = version_constraint[1:] 
    elif version_constraint.startswith('>='):
        min_version = version_constraint[2:]
    elif version_constraint.startswith('<='):
        max_version = version_constraint[2:]
    elif version_constraint.startswith('<'):
        max_version = version_constraint[1:]

    for version in sorted(packages[package_name].keys()):
        if is_compatible(version, min_version, max_version) and package_name not in resolved:
            if check_package_dependencies(package_name, version, resolved):
                return True
    return False

def check_package_dependencies(package_name, version, resolved):
    if package_name in resolved:
        return True

    for dep_pkg, dep_version in packages[package_name][version]['dependencies'].items():
        if not find_compatible_version(dep_pkg, dep_version, resolved):
            return False  

    resolved[package_name] = version
    return True

resolved_set = {}
root_version = '1.0.0'
if check_package_dependencies('root', root_version, resolved_set):
    print("Совместимые версии пакетов:")
    for pkg, ver in resolved_set.items():
        print(f"Пакет: {pkg}, Версия: {ver}")
else:
    print("Not found")
```
![image](https://github.com/user-attachments/assets/744e650c-5a4b-4132-9639-e1fdd527a79e)

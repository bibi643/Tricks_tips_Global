# Os Library
Youtube videos used are 
- [Os Module](https://www.youtube.com/watch?v=tJxcKyFMTGo&list=PLHYCooaMYBEzDrA_LnSqLqBYs17Y3EKkP&index=37)
- [Bonus](https://www.youtube.com/watch?v=ve2pmm5JqmI&list=PLHYCooaMYBEzDrA_LnSqLqBYs17Y3EKkP&index=41)
# Overview

Os library is made to interact with the os in different ways
- Navigate the file system
- Get file info
- Move file...

No need to pip install as it is built-in -> import os is enough

# Directories-Folders

## Current working directory (os.getcwd())

```python
print(os.getcwd())
```

## Navigation to/in a directory (os.chdir())
We need to pass the path as a string inside the function to move to the specific directory. We can check if it worked doing a getcwd() afterwards.
```python
os.chdir('path_of_the_file')

print(os.getcwd())
```

## List the files/folder in a directory (os.listdir())
You can pass a path to list a specific directory, but by default it is listing the current wroking directory.

It returns a list of the different files/folder in the directory.


```python
print(os.listdir())
```


## Creating a new directory (2 methods)

### os.mkdir('Directory_name')

```python
os.mkdir('OS_Demo_dir') #to create a folder called OS_Demo_dir
```

### os.makedirs('Directory_Name')
This creates directory **AND** subdirectories.
```python
os.makedirs('New_Directory') # Create a new directory calle New_directory.
os.makedirs('dir1/subdir1' # Create the dir1 and subdir1 which cannot be done with mkdir()
```

## Removing directories (2 methods)
### os.rmdir('...')
```python
os.rmdir('name_directory')

```
### os.removedirs('...')

```python
os.removedirs('name_directory/name_subdir')
```

# Files

## Rename(os.rename())
```python
os.rename('old_file.txt','new_file.txt')
```
This rename the file old_file to a file new_file.

## Info about a file (os.stat())

```python
from datetime import datetime

modif_time=os.stat('file_name.txt').st_mtime
print(datetime.fromtimestamp(modif_time))
>>> 2016-04-14 19:21:55
```
# Traverse all the tree (os.walk())
os.walk() returns a tuple of 3 parts.

```python
for dirpath, dirnames, filenames in os.walk(os.getcwd()):
	print('Current Path:', dirpath)
	print('Directories:', dirnames)
	print('Files:', filenames)
```

It returns for each path, all the folders and files in it. 
Then it goes into the first folder and return the path and all the folders and files into it...

# Environment Variable

```python
os.environ.get('HOME)')
```

# os.path

### Create a file in home directory
Create a path joining a path and a file name.

os.path.join(path,file) takes 2 arguments, the path where we want to create the file and the file name with extension.
We need to apply the with open after to really create the file.
```python
file_path=os.path.join(os.environ.get('HOME'),'text.txt')
with open( file_path,'w') as f:
	f.write()
```

### Grab base name / dirname
- Base Name of a file (**os.path.basename()**)


```python
os.path.basename('/tmp/test.txt')
>>> text.txt

```

- Directory name (**os.path.dirname()**)


```python
os.path.dirname('/tmp/test.txt')
>>> /tmp
```

- Tuple returning both ('dir_name','file') **(using os.path.split() or os.path.splitext())**
 splitext splits the root of the path and the extension into a tuple 

```python
os.path.splitext('/tmp/test.txt')
>>> ('/tmp/test', '.txt')
```

```python
os.path.split('/tmp/test.txt')
>>>('/tmp', 'test.txt')
```


# Check if a path/dir/file exist (os.path.isfile(), .path.isdir(), .path.exists())

```python
os.path.exists('/tmp/test.txt')
os.path.isdir('...')
os.path.isfile('...')

```

# Recall
dir(os) will return all the command for this specific module.

```python
import os
print(dir(os))
```

# Bonus Automate Parsing an renaming Multiple files

## Problematic 
Rename and sort a bunch of files, such as photos, videos files...

```python
import os
os.chdir('path_to_the_dir_we_want)
print(os.getcwd()) # to check we are in the right directory
for f in os.listdir():
 
  # split extension
  file_name, file_ext= os.path.splitext(f)

  # Extract the different information from the file_name
  f_title, f_course, f_num = file_name.split('-')

  # Remove any whitespace at the beginning and the end
  f_title= f_title.strip()
  f_course= f_course.strip()
  f_num = f_num.strip()

**zfill(n=width of the string)** this would convert the numbers 1 -> 01 if we put zfill(2).
  f_num= f_num.zfill(2)

  # Reformatting as we want
  new_name='{}-{}-{}{}'.format(f_num,f_course,f_title,f_ext)
  os.rename(f, new_name)
```

  

  

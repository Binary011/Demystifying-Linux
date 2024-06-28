#!/usr/bin/python3

import sys
import subprocess

def compile_and_execute(filename, debug=False):
    file_extension = filename.split('.')[-1].lower()

    if file_extension == 'c':
        compiler = 'gcc'
        executable = filename.split('.')[0]
        args = [compiler, filename, '-o', executable]
        subprocess.run(args)
        if debug:
            subprocess.run(['gdb', '-q', '--args', './' + executable])
        else:
            subprocess.run(['./' + executable])

    elif file_extension == 'cpp':
        compiler = 'g++'
        executable = filename.split('.')[0]
        args = [compiler, filename, '-o', executable]
        subprocess.run(args)
        if debug:
            subprocess.run(['gdb', '-q', '--args', './' + executable])
        else:
            subprocess.run(['./' + executable])

    elif file_extension == 'java':
        subprocess.run(['javac', filename])
        java_class = filename.split('.')[0]
        subprocess.run(['java', java_class])

    else:
        print("Unsupported file extension:", file_extension)

if len(sys.argv) < 2:
    print("Usage: python compile_and_execute.py <filename> [--debug]")
    sys.exit(1)

filename = sys.argv[1]
debug = False
if len(sys.argv) == 3 and sys.argv[2] == '--debug':
    debug = True

compile_and_execute(filename, debug)

import os

env = Environment(ENV = os.environ)
env.Append(CPPPATH = ['include'])
env.Append(CCFLAGS = '-g -Wall -O0'.split())
env.Append(LIBS    = ['m'])
env.Append(RPATH   = '.')
env.SharedLibrary('dubins', ['src/dubins.c'])

appenv = env.Clone()
appenv.Append(LIBS    = ['dubins'])
appenv.Append(LIBPATH = ['.'])
demo = appenv.Program('demo_app', ['demos/demo.c'])
test = appenv.Program('test_app', ['tests/test.c'])
testcli = appenv.Program('test_cli', ['tests/test-cli.c'])

Depends(demo, 'libdubins.so')
Depends(test, 'libdubins.so')
Depends(testcli, 'libdubins.so')

prefix = '/home/ehuang/local'
lib_dir = os.path.join(prefix, 'lib')
include_dir = os.path.join(prefix, 'include')
env.Alias('install', env.Install(lib_dir, 'libdubins.so'))
env.Alias('install', env.Install(include_dir, 'include/dubins.h'))

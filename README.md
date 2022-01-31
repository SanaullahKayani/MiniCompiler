# MiniCompiler 

The .NET Framework provides the ICodeCompiler compiler execution interface.
The CSharpCodeProvider class implements this interface and provides access to instances
of the C# code generator and code compiler. The following sample code creates an
instance of CSharpCodeProvider and uses it to get a reference to a ICodeCompiler
interface.
CSharpCodeProvider codeProvider = new CSharpCodeProvider();
ICodeCompiler icc = codeProvider.CreateCompiler();
Once you have a reference to an ICodeCompiler interface, you can use it to compile your
source code. You will pass parameters to the compiler by using
the CompilerParameters class. Here is an example:
System.CodeDom.Compiler.CompilerParameters parameters = new
CompilerParameters();
parameters.GenerateExecutable = true;
parameters.OutputAssembly = Output;
CompilerResults results =
icc.CompileAssemblyFromSource(parameters,SourceString);
The code above uses the CompilerParameters object to tell the compiler that you want to
generate an executable file (as opposed to a DLL) and that you want to output the resulting
assembly to disk. The call to CompileAssemblyFromSource is where the assembly gets
compiled. This method takes the parameters object and the source code, which is a string.
After you compile your code, you can check to see if there were any compilation errors. You
use the return value from CompileAssemblyFromSource, which is a CompilerResults object.
This object contains an errors collection, which contains any errors that occurred during the
compile.

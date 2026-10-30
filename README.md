# GitHub Actions Practice — DevFlow

Бұл жоба 3.1.46, 3.1.47 және 3.1.48 тақырыптарындағы практикалық тапсырмаларды орындауға арналған.

## Жоба құрылымы

```text
github-actions-practice/
├── .github/
│   └── workflows/
│       ├── first-workflow.yml
│       └── web-project.yml
├── index.html
├── style.css
└── README.md
```

## 1. 3.1.46 — GitHub Actions жұмыс принципі

`index.html` файлы репозиторийге қосылады. `first-workflow.yml` Workflow-ы `main` тармағына Push жасалғанда автоматты түрде іске қосылады. Оны Actions → Student Workflow бөлімінен көруге болады.

**GitHub Actions қолданудың 3 артықшылығы:**
1. Қайталанатын тексерулерді автоматты орындап, уақытты үнемдейді.
2. Қателерді жобаға өзгеріс енгізілгеннен кейін ерте анықтайды.
3. Тестілеу мен жариялау процесін біріздендіріп, қолмен орындалатын жұмысты азайтады.

## 2. 3.1.47 — алғашқы Workflow құру

`.github/workflows/first-workflow.yml` ішінде `Student Workflow` құрылған. Ол студент туралы және жоба туралы хабарламаны шығарады, күн мен операциялық жүйе туралы ақпаратты көрсетеді және репозиторий файлдарының тізімін шығарады.

## 3. 3.1.48 — YAML арқылы веб-жобаны тексеру

`.github/workflows/web-project.yml` файлында `Web Project Check` Workflow-ы берілген. Ол:
- репозиторийді `actions/checkout@v4` арқылы жүктейді;
- терминалдағы файлдар тізімін көрсетеді;
- `index.html` файлының бар-жоғын тексереді;
- `style.css` файлының бар-жоғын тексереді;
- HTML ішінде `style.css` дұрыс қосылғанын тексереді.

Егер қажетті файл табылмаса, тиісті Step `exit 1` арқылы қатемен аяқталады. Файлдар дұрыс болса, соңғы Step сәтті орындалады.

## GitHub-қа жүктеу

1. GitHub-та `github-actions-practice` атты жаңа **Public** немесе **Private** репозиторий жасаңыз. README файлын GitHub-та алдын ала құру міндетті емес.
2. Осы жоба бумасын VS Code арқылы ашыңыз.
3. VS Code терминалында төмендегі командаларды орындаңыз (USERNAME орнына GitHub логиніңізді жазыңыз):

```bash
git init
git branch -M main
git add .
git commit -m "Add GitHub Actions practice project"
git remote add origin https://github.com/USERNAME/github-actions-practice.git
git push -u origin main
```

Егер `remote origin already exists` қатесі шықса, мына команданы қолданыңыз:

```bash
git remote set-url origin https://github.com/USERNAME/github-actions-practice.git
git push -u origin main
```

## Workflow нәтижесін көру

GitHub репозиторийін ашыңыз → **Actions** бөліміне кіріңіз → `Student Workflow` және `Web Project Check` атауларын таңдаңыз → соңғы іске қосылуды ашыңыз. Жасыл белгі — Success, қызыл белгі — Failure.

## Қосымша тапсырма: CSS файлы жоқ кездегі қатені тексеру

Бұл сынақты негізгі жұмысты сәтті өткізгеннен кейін ғана орындаңыз:

```bash
git rm style.css
git commit -m "Test missing CSS validation"
git push
```

`Web Project Check` Workflow-ы `Check CSS file` қадамында **Failure** көрсетуі керек. Бұл — күтілетін сынақ нәтижесі.

CSS файлын қалпына келтіру:

```bash
git checkout HEAD~1 -- style.css
git add style.css
git commit -m "Restore CSS file"
git push
```

Соңғы Push-тан кейін Workflow қайтадан **Success** болуы керек.

## Скриншотқа түсірілетін нәтижелер

Оқытушыға тапсыру үшін өз GitHub аккаунтыңыздан мына скриншоттарды түсіріңіз:
1. Репозиторийдің файлдар құрылымы (`index.html`, `style.css`, `.github/workflows`).
2. `Student Workflow` сәтті орындалған Actions нәтижесі.
3. `Web Project Check` сәтті орындалған Actions нәтижесі.
4. CSS файлын уақытша алып тастағандағы `Failure` нәтижесі.
5. CSS қалпына келтірілгеннен кейінгі `Success` нәтижесі.

> Ескерту: GitHub-тағы нақты орындалу скриншоттарын репозиторийді өз аккаунтыңызға жүктеп, Workflow іске қосылғаннан кейін түсіру қажет.

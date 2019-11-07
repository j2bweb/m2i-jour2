# m2i-jour2
1
00j2bweb/m2i-jour2
 Code Issues 0 Pull requests 0 Projects 0 Wiki Security Insights Settings
No description, website, or topics provided.
 3 commits
 2 branches
 0 releases
 1 contributor
Your recently pushed branches:

 cherry (40 minutes ago)
Julien BOUCHAREINE
Julien BOUCHAREINE Readme modified
Latest commit
98889d3
1 hour ago
Type	Name	Latest commit message	Commit time
logs	Init branch hotfix	1 hour ago
.gitignore	Init branch hotfix	1 hour ago
README.md	Readme modified	1 hour ago
 README.md
 Welcome to the m2i-jour2 wiki!
Wikis provide a place in your repository to lay out the roadmap of your project, show the current status, and document software better, together.
Particularités techniques
Similaire en cela à BitKeeper, Git ne repose pas sur un serveur centralisé, mais il utilise un système de connexion pair à pair. Le code informatique développé est stocké non seulement sur l’ordinateur de chaque contributeur du projet, mais il peut également l'être sur un serveur dédié. C'est un outil de bas niveau, qui se veut simple et performant, dont la principale tâche est de gérer l'évolution du contenu d'une arborescence.

Git indexe les fichiers d'après leur somme de contrôle calculée avec la fonction de hachage SHA-1. Quand un fichier n'est pas modifié, la somme de contrôle ne change pas et le fichier n'est stocké qu'une seule fois. En revanche, si le fichier est modifié, les deux versions sont stockées sur le disque.

Contrastant avec les architectures de logiciel de gestion de versions habituellement utilisées jusqu'alors, Git repose entièrement sur un petit nombre de structures de données élémentaires. Linus Torvalds expliquait ainsi : « Par bien des aspects, vous pouvez considérer git comme un simple système de fichiers. Il est adressé par contenu, et possède la notion de versionnage, mais je l'ai vraiment conçu en prenant le point de vue d'un spécialiste des systèmes de fichiers (après tout, j'ai l'habitude de travailler sur des noyaux) et je n'avais absolument aucune envie de créer un système de gestion de version traditionnel. »6 Les premières versions de Git offraient une interface rudimentaire pour manipuler ces objets internes avant que les fonctionnalités courantes de gestion de version ne soient ensuite progressivement ajoutées et raffinées.

Git est considéré comme performant, au point que certains autres logiciels de gestion de version (Darcs, Arch), qui n'utilisent pas de base de données, se sont montrés intéressés par le système de stockage des fichiers de Git pour leur propre fonctionnement7,8. Ils continuent toutefois à proposer des fonctionnalités plus évoluées.

Dès le début, Git a été pensé dans le but de fonctionner de façon décentralisée, c'est d'ailleurs l'une des clefs de son succès[réf. souhaitée]. La décentralisation de Git a aussi beaucoup apporté au développement des logiciels libres, puisque le besoin de demander un compte sur un dépôt SVN ou CVS centralisé devient obsolète. Il suffit de forker un projet ou de le cloner pour commencer à travailler dessus (avec tout l'historique du projet en local) et ensuite de proposer sa contribution (pull request) au dépôt principal (mainteneur principal du projet).

Les serveurs Git utilisent par défaut le port 9418 pour le protocole spécifique à Git. Les protocoles HTTP, HTTPS et SSH (et leurs ports standards) peuvent aussi être utilisés.

Fonctionnement
Git possède deux structures de données : une base d'objets et un cache de répertoires. Il existe cinq types d'objets :

l'objet blob (pour binary large object désignant un ensemble de données brutes9), qui représente le contenu d'un fichier ;
l'objet tree (mot anglais signifiant arbre), qui décrit une arborescence de fichiers. Il est constitué d'une liste d'objets de type blobs et des informations qui leur sont associées, tel que le nom du fichier et les permissions. Il peut contenir récursivement d'autres trees pour représenter les sous-répertoires ;
l'objet commit (résultat de l'opération du même nom signifiant « valider une transaction »10), qui correspond à une arborescence de fichiers (tree) enrichie de métadonnées comme un message de description, le nom de l'auteur, etc. Il pointe également vers un ou plusieurs objets commit parents pour former un graphe d'historiques9 ;
l'objet tag (étiquette) qui est une manière de nommer arbitrairement un commit spécifique pour l'identifier plus facilement. Il est en général utilisé pour marquer certains commits, par exemple par un numéro ou un nom de version (2.1 ou bien Lucid Lynx);
l'objet branch (branche) qui contient une partie de l'avancement du projet. Les branches sont souvent utilisées pour avancer dans une partie du projet sans impacter une autre partie.
La base des objets peut contenir n'importe quel type d'objets. Une couche intermédiaire, utilisant des index (les sommes de contrôle), établit un lien entre les objets de la base et l'arborescence des fichiers.

Chaque objet est identifié par une somme de contrôle SHA-1 de son contenu. Git calcule la somme de contrôle et utilise cette valeur pour déterminer le nom de fichier de l'objet. L'objet est placé dans un répertoire dont le nom correspond aux deux premières lettres de la somme de contrôle. Le reste de la somme de contrôle constitue alors le nom du fichier pour cet objet.

Git enregistre chaque révision dans un fichier en tant qu'objet blob unique. Les relations entre les objets blobs sont déterminées en examinant les objets commit. En général, les objets blobs sont stockés dans leur intégralité en utilisant la compression de la zlib. Ce principe peut rapidement consommer une grande quantité de place disque ; de ce fait, les objets peuvent être combinés dans des archives, qui utilisent la compression différentielle (c'est-à-dire que les blobs sont enregistrés sous la forme de différences par rapport aux autres blobs).

Quelques commandes
Git dispose notamment des commandes suivantes :

git init​ crée un nouveau dépôt ;
git clone​ clone un dépôt distant ;
git add​ ajoute de nouveaux objets blobs dans la base des objets pour chaque fichier modifié depuis le dernier commit. Les objets précédents restent inchangés ;
git commit​ intègre la somme de contrôle SHA-1 d'un objet tree et les sommes de contrôle des objets commits parents pour créer un nouvel objet commit ;
git branch​ liste les branches ;
git merge​ fusionne une branche dans une autre ;
git rebase​ déplace les c

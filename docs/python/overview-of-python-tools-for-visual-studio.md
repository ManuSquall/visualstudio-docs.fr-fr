---
title: Vue d’ensemble de la prise en charge de Python dans Visual Studio sur Windows
description: Résumé des fonctionnalités Python disponibles dans Visual Studio, qui en font le meilleur IDE Python sur Windows (également appelé Python Tools pour Visual Studio, ou PTVS).
ms.date: 09/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: fe19c1239c2f08417b1b7ee76cb07ae150c891d1
ms.sourcegitcommit: 25fc9605ba673afb51a24ce587cf4304b06aa577
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47029145"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Utiliser Python dans Visual Studio sur Windows

Python est un langage de programmation très apprécié, car il est fiable, souple, simple d’emploi et utilisable sur tous les systèmes d’exploitation. Il est soutenu à la fois par une solide communauté de développeurs et par de nombreuses bibliothèques gratuites. Python prend en charge toutes les méthodes de développement, notamment les applications web, les services web, les applications de bureau, les scripts et le calcul scientifique, et il est utilisé par une multitude d’universités, de scientifiques et de développeurs aussi bien occasionnels que professionnels. Pour plus d’informations sur ce langage, consultez le site [python.org](https://www.python.org) et la page [Python for Beginners](https://www.python.org/about/gettingstarted/) (Débuter avec Python).

Visual Studio est un puissant IDE Python sur Windows. Visual Studio offre une prise en charge [open source](https://github.com/Microsoft/ptvs) du langage Python via les charges de travail **Développement Python** et **Science des données** (Visual Studio 2017), ainsi que l’extension gratuite Python Tools pour Visual Studio (Visual Studio 2015 et versions antérieures).

Python n’est actuellement pas pris en charge dans Visual Studio pour Mac, mais est disponible sur Mac et Linux via Visual Studio Code (consultez les [questions et réponses](#questions-and-answers)).

Pour commencer :

- Suivez les [instructions d’installation](installing-python-support-in-visual-studio.md) pour configurer la charge de travail Python.
- Familiarisez-vous avec les fonctionnalités Python de Visual Studio en parcourant les sections de cet article. Vous pouvez également [Regarder une série de vidéos (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) pour une présentation de Python dans Visual Studio (22 minutes au total).
- Suivez un ou plusieurs guides de démarrage rapide pour créer un projet. Si vous ne savez pas comment, commencez par [Créer une application web avec Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
- Suivez le tutoriel [Utiliser Python dans Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) pour une expérience utilisateur complète.

## <a name="support-for-multiple-interpreters"></a>Prise en charge de plusieurs interpréteurs

La fenêtre **Environnements Python** de Visual Studio (illustrée ci-dessous dans une large vue développée) vous fournit un emplacement unique pour gérer tous vos environnements Python généraux, environnements conda et environnements virtuels. Visual Studio détecte automatiquement les installations de Python à des emplacements standard et vous permet de configurer des installations personnalisées. Avec chaque environnement, vous pouvez facilement gérer les packages, ouvrir une fenêtre interactive pour cet environnement et accéder aux dossiers de l’environnement.

![Vue développée de la fenêtre Environnements Python](media/environments-expanded-view.png)

Utilisez la commande **Ouvrir une fenêtre interactive** pour exécuter Python en mode interactif dans le contexte de Visual Studio. Utilisez la commande **Ouvrir dans PowerShell** pour ouvrir une fenêtre de commande distincte dans le dossier de l’environnement sélectionné. À partir de cette fenêtre de commande, vous pouvez exécuter n’importe quel script Python. 

Pour plus d'informations :

- Vidéo (2 min 35 s) : [Gérer les environnements Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567)
- Documentation : [Gérer les environnements Python](managing-python-environments-in-visual-studio.md)
- Documentation : [Référence sur les environnements Python](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Large éventail de fonctionnalités de modification, IntelliSense et d’inclusion de code

Visual Studio fournit un éditeur Python de première classe, notamment la coloration syntaxique, la saisie semi-automatique dans l’ensemble du code et des bibliothèques, la mise en forme du code, l’aide sur les signatures, la refactorisation, la validation lint et les affinages de type. Visual Studio fournit également des fonctionnalités uniques, telles que l’affichage de classes, **Atteindre la définition**, **Rechercher toutes les références** et les extraits de code. L’intégration directe à la [fenêtre Interactive](#interactive-window) vous permet de développer rapidement du code Python déjà enregistré dans un fichier.

![Complétions de code pour le code Python dans Visual Studio](media/code-editing-completions-simple.png)

Pour plus d'informations :

- Vidéo (2 min 30 s) : [Modifier le code Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=r2iQH5LWE_4605918567)
- Documentation : [Modifier le code Python](editing-python-code-in-visual-studio.md)
- Documentation : [Code du format](formatting-python-code.md)
- Documentation : [Refactoriser du code](refactoring-python-code.md)
- Documentation : [Utiliser un linter](linting-python-code.md)
- Documentation générale sur les fonctionnalités Visual Studio : [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Fenêtre Interactive

Pour chaque environnement Python connu de Visual Studio, vous pouvez facilement ouvrir le même environnement interactif (REPL) pour un interpréteur Python directement dans Visual Studio, au lieu d’utiliser une invite de commandes distincte. Vous pouvez aussi facilement basculer entre les environnements. (Pour ouvrir une invite de commandes distincte, sélectionnez votre environnement souhaité dans la fenêtre **Environnements Python**, puis sélectionnez la commande **Ouvrir dans PowerShell** comme expliqué précédemment sous [Prise en charge de plusieurs interpréteurs](#support-for-multipleiinterpreters).)

![Fenêtre interactive Python dans Visual Studio](media/interactive-window.png)

Visual Studio fournit également une intégration étroite entre l’éditeur de code Python et la fenêtre **Interactive**. Le raccourci clavier **Ctrl**+**Entrée** permet d’envoyer de façon pratique la ligne de code active (ou le bloc de code actif) dans l’éditeur vers la fenêtre **Interactive**, avant de passer à la ligne suivante (ou au bloc suivant). **Ctrl**+**Entrée** vous permet d’exécuter le code pas à pas en toute simplicité, sans avoir à exécuter le débogueur. Vous pouvez également envoyer le code sélectionné vers la fenêtre **Interactive** avec la même séquence de touches, et coller facilement ce code de la fenêtre **Interactive** vers l’éditeur. Ensemble, ces fonctionnalités vous permettent de traiter les détails d’un segment de code dans la fenêtre **Interactive** et d’enregistrer aisément les résultats dans un fichier au sein de l’éditeur.

Visual Studio prend également en charge IPython/Jupyter dans l’environnement REPL, notamment les tracés inline, .NET et WPF (Windows Presentation Foundation).

Pour plus d'informations :

- Vidéo (2 min 22 s : [Fenêtre Interactive Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=gJYKY5LWE_4605918567)
- Documentation : [Fenêtre Interactive](python-interactive-repl-in-visual-studio.md)
- Documentation : [IPython dans Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Système de projet, et modèles de projet et d’élément

Visual Studio vous permet de gérer la complexité d’un projet à mesure qu’il croît. Un projet contient bien plus qu’une structure de dossiers : il inclut une présentation de la façon dont les différents fichiers sont utilisés et comment ils sont liés entre eux. Visual Studio vous permet de distinguer le code d’application, le code de test, les pages web, JavaScript, les scripts de génération, entre autres, qui activent ensuite des fonctionnalités propres aux fichiers. Une solution Visual Studio, en outre, vous permet de gérer plusieurs projets associés, comme un projet Python et un projet d’extension C++.

![Solution Visual Studio contenant à la fois des projets Python et C++](media/projects-solution-explorer-two-projects.png)

Les modèles de projet et d’élément automatisent le processus de configuration des différents types de projets et de fichiers, ce qui vous fait gagner un temps précieux et vous évite d’avoir à gérer des détails complexes et sujets aux erreurs. Visual Studio fournit des modèles pour le web, Azure, la science des données, la console et d’autres types de projets, ainsi que des modèles pour les fichiers comme les classes Python, les tests unitaires, la configuration web Azure, HTML et même les applications Django.

[![Modèles de projet et d’élément Python dans Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Pour plus d'informations :

- Documentation : [Gérer les projets Python](managing-python-projects-in-visual-studio.md)
- Documentation : [Référence de modèles d’élément](python-item-templates.md)
- Documentation : [Modèles de projet Python](managing-python-projects-in-visual-studio.md#project-templates)
- Documentation : [Utiliser C++ et Python](working-with-c-cpp-python-in-visual-studio.md)
- Documentation générale sur les fonctionnalités Visual Studio : [Modèles de projet et d’élément](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Documentation générale sur les fonctionnalités Visual Studio : [Solutions et projets dans Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Débogage complet

L’un des points forts de Visual Studio est son puissant débogueur. Pour Python en particulier, Visual Studio inclut le débogage en mode mixte Python/C++, le débogage à distance sur Linux, le débogage à distance sur Azure, le débogage dans la fenêtre **Interactive** et le débogage des tests unitaires Python.

![Débogueur Visual Studio pour Python affichant une fenêtre contextuelle d’exceptions](media/debugging-exception-popup.png)

Pour plus d'informations :

- Vidéo (3 minutes 32 secondes) : [Débogage Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=Ep5dp5LWE_3805918567)
- Documentation : [Déboguer Python](debugging-python-in-visual-studio.md)
- Documentation : [Débogage en mode mixte Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Documentation : [Débogage à distance sur Linux](debugging-python-code-on-remote-linux-machines.md)
- Documentation : [Débogage à distance sur Azure](debugging-remote-python-code-on-azure.md)
- Documentation générale sur les fonctionnalités Visual Studio : [Visite guidée des fonctionnalités du débogueur Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Outils de profilage avec rapports exhaustifs

Le profilage collecte les données relatives à l’utilisation de votre application. Visual Studio prend en charge le profilage avec les interpréteurs CPython et offre la possibilité de comparer les performances entre différentes séquences de profilage.

[![Résultats du profileur Visual Studio pour un projet Python](media/profiling-results.png)](media/profiling-results.png#lightbox)

Pour plus d'informations :

- Vidéo (3 minutes) : [Profilage Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=s6FoC6LWE_1005918567)
- Documentation : [Outils de profilage Python](profiling-python-code-in-visual-studio.md)
- Documentation générale sur les fonctionnalités Visual Studio : [Visite guidée des fonctionnalités de profilage](../profiling/profiling-feature-tour.md). (Certaines fonctionnalités de profilage Visual Studio ne sont pas disponibles pour Python.)

## <a name="unit-testing-tools"></a>Outils de test unitaire

Découvrez, exécutez et gérez les tests dans l’**Explorateur de tests** Visual Studio, et déboguez facilement les tests unitaires.

![Débogage d’un test unitaire Python dans Visual Studio](media/unit-test-debugging.png)

Pour plus d'informations :

- Vidéo (2 minutes 31 secondes) : [Test de Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=hb46k6LWE_405918567)
- Documentation : [Outils de test unitaire pour Python](unit-testing-python-in-visual-studio.md)
- Documentation générale sur les fonctionnalités Visual Studio : [Tests unitaires de votre code](../test/unit-test-your-code.md).

## <a name="publish-to-azure-and-azure-sdk-for-python"></a>Publier sur Azure et Azure SDK pour Python

Visual Studio assure la prise en charge intégrée de la publication des applications web et des services cloud sur Azure. Visual Studio inclut les modèles d’éléments *web.config* essentiels pour les contenus dynamique et statique. La charge de travail Python inclut également le kit SDK Azure pour Python, qui simplifie la consommation des services Azure à partir des applications Windows, Mac OS X et Linux.

![Publier l’application Python sur Azure dans Visual Studio](media/azure-publish-dialog.png)

Pour plus d'informations :

- Documentation : [Publier sur Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Documentation : [Kit SDK Azure pour Python](azure-sdk-for-python.md)

## <a name="python-training-on-microsoft-virtual-academy"></a>Formation Python sur Microsoft Virtual Academy

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo") | <ul><li>[Introduction à la programmation avec Python](https://mva.microsoft.com/en-US/training-courses/introduction-to-programming-with-python-8360?l=lqhuMxFz_8904984382)</li><li>[Débutant sur Python : chaînes et fonctions](https://mva.microsoft.com/en-US/training-courses/python-beginner-strings-and-functions-18015)</li><li>[Notions de base Python : liste et boucles](https://mva.microsoft.com/en-US/training-courses/python-fundamentals-lists-and-loops-18019)</li><li>[Principales questions sur Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121)</li></ul> |

## <a name="questions-and-answers"></a>Questions et réponses

**Q. Est que la prise en charge de Python est disponible avec Visual Studio pour Mac ?**

Un fichier . Pas pour l’instant, mais vous pouvez voter pour la demande sur [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac). La documentation [Visual Studio pour Mac](/visualstudio/mac/) identifie les types actuels de développement qu’il prend en charge. En attendant, Visual Studio Code sur Windows, Mac et Linux [fonctionne bien avec Python via les extensions disponibles](https://code.visualstudio.com/docs/languages/python).

**Q. Que puis-je utiliser pour créer une interface utilisateur avec Python ?**

Un fichier . Dans ce domaine, le principal moyen est d’utiliser [Qt Project](https://www.qt.io/qt-for-application-development/), avec des liaisons pour Python appelées [PySide (la liaison officielle)](https://wiki.qt.io/PySide) (consultez également les [téléchargements PySide](https://download.qt.io/official_releases/pyside/.)) et [PyQt](https://wiki.python.org/moin/PyQt). Pour l’instant, la prise en charge de Python dans Visual Studio n’inclut pas d’outils spécifiques pour le développement d’interface utilisateur.

**Q. Un projet Python peut-il produire un exécutable autonome ?**

Un fichier . Python est généralement un langage interprété, avec lequel le code est exécuté à la demande dans un environnement approprié prenant en charge le langage Python tel que Visual Studio et les serveurs web. Visual Studio ne fournit pas d’outils permettant de créer un exécutable autonome, qui désigne essentiellement un programme avec un interpréteur Python incorporé. La communauté Python a cependant fourni différents moyens de créer des exécutables sur [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython prend également en charge l’incorporation dans une application native, comme indiqué dans le billet de blog [Using CPython’s embeddable zip file](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/).

## <a name="features-matrix"></a>Tableau des fonctionnalités

Les fonctionnalités de Python sont installables dans les éditions de Visual Studio ci-après, comme décrit dans le [guide d’installation](installing-python-support-in-visual-studio.md) :

- [Visual Studio 2017 (toutes éditions)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2015 (toutes éditions)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express pour le web, Update 2 ou version ultérieure
- Visual Studio 2013 Express pour Desktop, Update 2 ou version ultérieure
- Visual Studio 2013 (édition Pro ou version ultérieure)
- Visual Studio 2012 (édition Pro ou version ultérieure)
- Visual Studio 2010 SP1 (édition Pro ou version ultérieure ; .NET 4.5 requis)

Visual Studio 2015 et versions antérieures sont disponibles à l’adresse [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).

> [!Important]
> Les fonctionnalités sont entièrement prises en charge et uniquement tenues à jour pour la version la plus récente de Visual Studio. Les fonctionnalités sont disponibles dans les versions antérieures, mais elles ne sont pas activement tenues à jour.

| Prise en charge de Python | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Gérer plusieurs interpréteurs | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Détection automatique des interpréteurs courants | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Ajout d’interpréteurs personnalisés | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Environnements virtuels | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Pip/Facilité d’installation | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Système de projet | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Nouveau projet à partir du code existant | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Afficher tous les fichiers | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Contrôle de code source | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Intégration de Git | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| Modification | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Mise en surbrillance de la syntaxe | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Saisie semi-automatique | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Assistance pour la signature | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Info express | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Explorateur d’objets/Affichage de classes | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Barre de navigation | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Atteindre la définition | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Accéder à | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Rechercher toutes les références | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Mise en retrait automatique | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Mise en forme du code | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoriser - Renommer | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoriser - Extraire la méthode | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoriser - Ajouter/Supprimer à l’importation | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Fenêtre Interactive | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Fenêtre Interactive | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IPython avec graphiques inline | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Bureau | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Console/Application Windows | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| WPF IronPython (avec concepteur XAML) | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Windows Forms IronPython | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Web | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Projet web Django | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Projet Web Bottle | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Projet Web Flask | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Projet Web générique | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Déployer sur un site web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| Déployer sur un rôle web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Déployer sur un rôle de travail | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Exécution dans l’émulateur Azure | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Débogage distant | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| Attacher l’Explorateur de serveurs | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Modèles Django | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Débogage | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Saisie semi-automatique | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| Saisie semi-automatique pour CSS et JavaScript | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| Débogage | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Débogage | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Débogage sans projet | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Débogage - Attachement à la modification | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Débogage en mode mixte | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Débogage à distance (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Fenêtre interactive de débogage | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

<a name="matrix-profiling"></a>

| Profilage | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Profilage | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| Tester | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Explorateur de tests | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Exécuter le test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Déboguer le test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. Une prise en charge de Git pour Visual Studio 2012 est disponible dans l’extension Visual Studio Tools pour Git, accessible dans la [galerie Visual Studio](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit).

1. Le déploiement vers un site web Azure requiert le [kit SDK pour .NET 2.1 - Visual Studio 2010 SP1](https://go.microsoft.com/fwlink/?LinkId=313855). Les versions ultérieures ne prennent pas en charge Visual Studio 2010.

1. La prise en charge du rôle Web et du rôle de travail Azure nécessite le [kit SDK Azure pour .NET 2.3 - VS 2012](https://go.microsoft.com/fwlink/?LinkId=323511) ou une version ultérieure.

1. La prise en charge du rôle Web et du rôle de travail Azure nécessite le [kit SDK Azure pour .NET 2.3 - VS 2013](https://go.microsoft.com/fwlink/?LinkId=323510) ou une version ultérieure.

1. L’éditeur de modèle Django dans Visual Studio 2013 présente certains problèmes connus qui sont résolus par l’installation d’Update 2.

1. Requiert Windows 8 ou une version ultérieure. Visual Studio 2013 Express pour le web ne comporte pas la boîte de dialogue **Attacher au processus**. Toutefois, le débogage à distance du site web Azure reste possible à l’aide de la commande **Attacher le débogueur (Python)** dans l’**Explorateur de serveurs**. Le débogage à distance nécessite le [kit SDK Azure pour .NET 2.3 - Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=323510) ou une version ultérieure.

1. Requiert Windows 8 ou une version ultérieure. La commande **Attacher le débogueur (Python)** dans l’**Explorateur de serveurs** nécessite le [kit Azure SDK pour .NET 2.3 - Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=323510) ou une version ultérieure.

1. Requiert Windows 8 ou une version ultérieure.

## <a name="additional-resources"></a>Ressources supplémentaires

- [WFastCGI bridge between IIS and Python](https://pypi.org/p/wfastcgi) (pypi.org)
- [Cours Python gratuits sur Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Principales questions sur Python sur Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions)

---
title: "Python dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: 8cd00fe33cf463227dd09f93047350a96cee3b92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-python-in-visual-studio"></a>Utilisation de Python dans Visual Studio

Python est un langage de programmation très apprécié, car il est fiable, souple, simple d’emploi et utilisable sur tous les systèmes d’exploitation. Il est soutenu à la fois par une solide communauté de développeurs et par de nombreuses bibliothèques gratuites. Python prend en charge toutes les méthodes de développement, notamment les applications Web, les services web, les applications de bureau, les scripts et le calcul scientifique, et il est utilisé par une multitude d’universités, de scientifiques et de développeurs aussi bien occasionnels que professionnels. Pour plus d’informations sur ce langage, consultez le site [python.org](https://www.python.org) et la page [Python for Beginners](https://www.python.org/about/gettingstarted/) (Débuter avec Python).

Visual Studio sur Windows offre une prise en charge [open source](https://github.com/Microsoft/ptvs) du langage Python par le biais des charges de travail de développement et de science des données Python (Visual Studio 2017) et de l’extension gratuite Python Tools pour Visual Studio (Visual Studio 2015 et versions antérieures). Python n’est actuellement pas pris en charge dans Visual Studio pour Mac, mais est disponible sur Mac et Linux via Visual Studio Code (consultez [Questions et réponses ci-dessous](#questions-and-answers).

Pour commencer :

- Suivez les [instructions d’installation](installation.md) pour configurer la charge de travail Python
- Suivez un ou plusieurs guides de démarrage rapide pour créer un projet. Si vous n’êtes pas sûr, commencez par [Créer un projet à partir d’un modèle](quickstart-02-project-from-template.md).
- Suivez le didacticiel [Utilisation de Python dans Visual Studio](vs-tutorial-01-01.md) pour une expérience de bout en bout.
- Utilisez ensuite les liens ci-dessous pour explorer les fonctionnalités Python et les fonctionnalités de Visual Studio lui-même.

| Fonctionnalité | Description | Documentation générale de Visual Studio | 
| --- | --- | --- |
| [Système de projet Visual Studio](python-projects.md) | Récupère implicitement une structure de dossiers de code Python tout en autorisant un contrôle explicite permettant d’identifier le code d’application, le code de test, les pages web, JavaScript, les scripts de build, etc. | [Solutions et projets dans Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Modèles de projet](python-projects.md#project-templates) | Crée rapidement une structure de projet de type console, web, Azure, science des données et autres. | [Modèles Visual Studio](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| Prise en charge d’interpréteurs multiples | Prend en charge plusieurs versions de CPython et d’IronPython. | N/A |
| Prise en charge d’IPython | Inclut la prise en charge d’IPython/Jupyter dans la boucle REPL pour les tracés inline, .NET et Windows Presentation Foundation (WPF). | N/A |
| [Large éventail de fonctionnalités de modification, IntelliSense et d’inclusion de code](code-editing.md) | Inclut la coloration syntaxique, la saisie semi-automatique dans l’ensemble du code et des bibliothèques, la [mise en forme du code](code-formatting.md), une assistance pour la signature, l’affichage de classes, les fonctions Atteindre la définition et Rechercher toutes les références, les extraits de code, la [refactorisation](code-refactoring.md), [PyLint](code-pylint.md), etc. | [Écriture de code dans l’éditeur de code et de texte](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Fenêtre interactive](interactive-repl.md) | Offre une expérience REPL rapide pour Python en facilitant la mise en surbrillance d’une partie de votre code et son envoi à la fenêtre interactive. | N/A |
| [Débogage complet](debugging.md) | Le débogage peut être effectué avec ou sans projet Visual Studio et peut prendre la forme d’un débogage d’exécutables existants, d’un [débogage en mode mixte Python/C++](debugging-mixed-mode.md), d’un [débogage à distance](debugging-cross-platform-remote.md) dans Windows/Linux/Mac, d’un [débogage à distance dans Azure](debugging-azure-remote.md) et d’un débogage dans la fenêtre interactive. | [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md) |
| [Outils de profilage avec rapports exhaustifs](profiling.md) | Collectent les données relatives à l’utilisation de votre application, en permettant notamment de comparer les performances entre différentes séquences de profilage. | [Outils de profilage](../profiling/profiling-tools.md) (certaines fonctionnalités de profilage Visual Studio ne sont pas disponibles pour Python) |
| [Outils de test unitaire](unit-testing.md) | Permettent de découvrir, exécuter et gérer des tests dans l’Explorateur de tests Visual Studio, et de déboguer aisément des tests unitaires. | [Tests unitaires sur votre code](../test/unit-test-your-code.md) |

La charge de travail Python inclut également le [kit SDK Azure pour Python](azure-sdk-for-python.md), qui simplifie la consommation des services Azure à partir des applications Windows, Mac OS X et Linux.

Pour une présentation vidéo, consultez le cours [Python Tools pour Visual Studio](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) sur Microsoft Virtual Academy (environ 22 minutes au total). 

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]


## <a name="questions-and-answers"></a>Questions et réponses

**Q. Est que la prise en charge de Python est disponible avec Visual Studio pour Mac ?**

Un fichier . Pas pour l’instant, même si elle est demandée sur [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac). La documentation [Visual Studio pour Mac](https://docs.microsoft.com/visualstudio/mac/) identifie les types actuels de développement qu’il prend en charge. En attendant, Visual Studio Code sur Windows, Mac et Linux [fonctionne bien avec Python via les extensions disponibles](https://code.visualstudio.com/docs/languages/python).

**Q. Que puis-je utiliser pour créer une interface utilisateur avec Python ?**

Un fichier . Dans ce domaine, le principal moyen est d’utiliser [Qt Project](https://www.qt.io/qt-for-application-development/), avec des liaisons pour Python appelées [PySide (la liaison officielle)](http://wiki.qt.io/PySide) (consultez également les [téléchargements PySide](https://download.qt.io/official_releases/pyside/.)) et [PyQt](https://wiki.python.org/moin/PyQt). Pour l’instant, la prise en charge de Python dans Visual Studio n’inclut pas d’outils spécifiques pour le développement d’interface utilisateur.

**Q. Un projet Python peut-il produire un exécutable autonome ?**

Un fichier . Python est généralement un langage interprété, avec lequel le code est exécuté à la demande dans un environnement approprié prenant en charge le langage Python tel que Visual Studio et les serveurs web. Visual Studio ne fournit pas d’outils permettant de créer un exécutable autonome, qui désigne essentiellement un programme avec un interpréteur Python incorporé. Toutefois, la communauté Python décrit différents moyens de créer des exécutables sur [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython prend également en charge l’incorporation dans une application native, comme décrit dans le billet de blog, [Using CPython’s Embeddable Zip File](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/) (Utilisation d’un fichier zip incorporable dans CPython).

## <a name="features-matrix"></a>Tableau des fonctionnalités

La prise en charge de Python est installable dans les éditions de Visual Studio ci-après, comme décrit dans le [guide d’installation](installation.md) :

- [Visual Studio 2017 (toutes éditions)](https://www.visualstudio.com/vs/)
- [Visual Studio 2015 (toutes éditions)] (https://www.visualstudio.com/fr-fr/downloads/visual-studio-2015-downloads-vs)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express pour le web, Update 2 ou version ultérieure
- Visual Studio 2013 Express pour Desktop, Update 2 ou version ultérieure
- Visual Studio 2013 (édition Pro ou version ultérieure)
- Visual Studio 2012 (édition Pro ou version ultérieure)
- Visual Studio 2010 SP1 (édition Pro ou version ultérieure ; .NET 4.5 requis)

Fonctionnalités prises en charge par version et édition de Visual Studio :

| Prise en charge de Python | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Gestion d’interpréteurs multiples | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
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

| Fenêtre interactive | 2017 | 2015 | 2013 Comm | 2013 Desktop | 2013 web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Fenêtre interactive | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
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
| Attachement dans l’Explorateur de serveurs | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
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
| Fenêtre de débogage interactive | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

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

1. Une prise en charge de Git pour VS 2012 est disponible dans l’extension Visual Studio Tools pour Git, accessible dans la [galerie Visual Studio](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c).

2. Le déploiement vers un site web Azure requiert le [kit SDK pour .NET 2.1 - VS 2010 SP1](http://go.microsoft.com/fwlink/?LinkId=313855).  Les versions ultérieures ne prennent pas en charge Visual Studio 2010.

3. La prise en charge du rôle Web et du rôle de travail Azure nécessite le [kit SDK Azure pour .NET 2.3 - VS 2012](http://go.microsoft.com/fwlink/?LinkId=323511) ou une version ultérieure.

4. La prise en charge du rôle Web et du rôle de travail Azure nécessite le [kit SDK Azure pour .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) ou une version ultérieure.

5. L’éditeur de modèle Django dans Visual Studio 2013 présente certains problèmes connus qui sont résolus par l’installation d’Update 2.

6. Requiert Windows 8 ou une version ultérieure. Visual Studio 2013 Express pour le web ne comporte pas la boîte de dialogue Attacher au processus, mais le débogage à distance du site web Azure reste possible à l’aide de la commande Attacher le débogueur (Python) dans l’Explorateur de serveurs. Le débogage à distance nécessite le [kit SDK Azure pour .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) ou une version ultérieure.

7. Requiert Windows 8 ou une version ultérieure. La commande Attacher le débogueur (Python) dans l’Explorateur de serveurs requiert le [kit SDK Azure pour .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) ou une version ultérieure.

8. Requiert Windows 8 ou une version ultérieure.

## <a name="additional-resources"></a>Ressources supplémentaires

- [Writing Kinect games with Python using PyKinect](https://github.com/Microsoft/PTVS/wiki/PyKinect) (Écrire des jeux Kinect avec Python à l’aide de PyKinect) (wiki GitHub)
- [WFastCGI bridge between IIS and Python](https://pypi.python.org/pypi/wfastcgi) (Pont WFastCGI entre IIS et Python) (python.org)
- [Cours Python gratuits sur Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Principales questions sur Python sur Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions)

---
title: Installer la prise en charge de Python
description: Guide pratique pour installer Python Tools pour Visual Studio (PTVS) dans Visual Studio 2017, 2015, 2013, 2012 et 2010, y compris les options et les emplacements d’installation.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09fb452d579130cdf6597ada3af509b35f24ff43
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254808"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Guide pratique pour installer la prise en charge de Python dans Visual Studio sur Windows

Pour installer la prise en charge de Python pour Visual Studio (également appelé Python Tools pour Visual Studio ou PTVS), suivez les instructions de la section qui correspond à votre version de Visual Studio :

- [Visual Studio 2017 et Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 et versions antérieures](#visual-studio-2013-and-earlier)

Pour tester rapidement la prise en charge de Python après avoir suivi les étapes d’installation, ouvrez la fenêtre **interactive Python** en appuyant sur **ALT** + **I** et en entrant `2+2` . Si vous n’obtenez pas la sortie `4`, passez en revue la procédure que vous avez suivie.

> [!Tip]
> La charge de travail Python inclut la précieuse extension Cookiecutter qui fournit une interface utilisateur graphique permettant de découvrir les modèles, d’entrer les options de modèle et de créer des projets et des fichiers. Pour plus d’informations, consultez [Utiliser l’extension Cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> La prise en charge de Python n’est actuellement pas disponible dans Visual Studio pour Mac, mais elle est disponible sur Mac et Linux via Visual Studio Code. Consultez [questions et réponses](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 et Visual Studio 2017

1. Téléchargez et exécutez la dernière version de Visual Studio Installer. Si Visual Studio est déjà installé, exécutez Visual Studio Installer, sélectionnez l’option **Modifier** (consultez [Modifier Visual Studio](../install/modify-visual-studio.md)), puis accédez à l’étape 2.

    > [!div class="nextstepaction"]
    > [Installer la Communauté Visual Studio 2019](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > L’édition Community est destinée aux développeurs individuels, à l’apprentissage en classe, à la recherche académique et au développement open source. Pour les autres utilisations, installez [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) ou [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. Le programme d’installation vous présente une liste de charges de travail, qui sont des groupes d’options connexes pour des types de développement spécifiques. Pour Python, sélectionnez la charge de travail **Développement Python**.

    ![Charge de travail de développement Python dans le programme d’installation de Visual Studio](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    Facultatif : Si vous travaillez dans le domaine de la science des données, considérez également la charge de travail **Applications de science des données et analytiques**. Cette charge de travail inclut la prise en charge des langages Python, R et F#. Pour plus d’informations, consultez [Charge de travail Applications de science et analyse des données](data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Les charges de travail Python et Science des données ne sont disponibles qu’avec Visual Studio 2017 version 15.2 et version ultérieure.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Facultatif : Si vous travaillez dans le domaine de la science des données, considérez également la charge de travail **Applications de science des données et analytiques**. Cette charge de travail inclut la prise en charge des langages Python et F#. Pour plus d’informations, consultez [Charge de travail Applications de science et analyse des données](data-science-and-analytical-applications-workload.md).
    ::: moniker-end

1. Sur le côté droit du programme d’installation, choisissez d’options si vous le souhaitez. Ignorez cette étape pour accepter les options par défaut.

    ::: moniker range="vs-2017"
    ![Options de développement Python dans le programme d’installation de Visual Studio](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Options de développement Python dans le programme d’installation de Visual Studio 2019](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Option | Description |
    | --- | --- |
    | Distributions Python | Choisissez n’importe quelle combinaison des options disponibles, telles que les variantes 32 bits et 64 bits des distributions Python 2, Python 3, Miniconda, Anaconda2 et Anaconda3 avec lesquelles vous prévoyez de travailler. Chacune comprend l’interpréteur, le runtime et les bibliothèques de la distribution. Anaconda est une plateforme de science des données ouverte qui inclut une large gamme de packages préinstallés. (Vous pouvez revenir au programme d’installation de Visual Studio à tout moment pour ajouter ou supprimer des distributions.)  **Remarque**: Si vous avez installé une distribution en dehors du programme d’installation de Visual Studio, il n’est pas nécessaire de vérifier l’option équivalente ici. Visual Studio détecte automatiquement les installations existantes de Python. Consultez [Fenêtre Environnements Python](managing-python-environments-in-visual-studio.md#the-python-environments-window). En outre, si une version de Python plus récente que celle qui apparaît dans le programme d’installation est disponible, vous pouvez installer cette nouvelle version séparément ; Visual Studio la détectera. |
    | **Prise en charge des modèles Cookiecutter** | Installe l’interface utilisateur graphique Cookiecutter pour découvrir des modèles, entrer des options de modèle et créer des projets et fichiers. Consultez [Utiliser l’extension Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Prise en charge de Python web** | Installe des outils pour le développement web incluant la prise en charge de l’édition de code HTML, CSS et JavaScript, ainsi que des modèles pour des projets utilisant les frameworks Bottle, Flask et Django. Consultez [Modèles de projet web Python](python-web-application-project-templates.md). |
    | **Prise en charge de Python IoT** | Prend en charge le développement Windows IoT Core avec Python. |
    | **Outils de développement natifs Python** | Installe le compilateur C++ et d’autres composants nécessaires pour développer des extensions natives pour Python. Consultez [Créer une extension C++ pour Python](working-with-c-cpp-python-in-visual-studio.md). Installez également la charge de travail **Développement bureautique avec C++** pour bénéficier d’une prise en charge complète. |
    | **Outils principaux pour Azure Cloud Services** | Fournit une prise en charge supplémentaire pour le développement Azure Cloud Services en Python. Consultez [Projets Azure Cloud Service](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Option | Description |
    | --- | --- |
    | Distributions Python | Choisissez n’importe quelle combinaison des options disponibles, telles que les variantes 32 bits et 64 bits des distributions Python 2, Python 3, Miniconda, Anaconda2 et Anaconda3 avec lesquelles vous prévoyez de travailler. Chacune comprend l’interpréteur, le runtime et les bibliothèques de la distribution. Anaconda est une plateforme de science des données ouverte qui inclut une large gamme de packages préinstallés. (Vous pouvez revenir au programme d’installation de Visual Studio à tout moment pour ajouter ou supprimer des distributions.)  **Remarque**: Si vous avez installé une distribution en dehors du programme d’installation de Visual Studio, il n’est pas nécessaire de vérifier l’option équivalente ici. Visual Studio détecte automatiquement les installations existantes de Python. Consultez [Fenêtre Environnements Python](managing-python-environments-in-visual-studio.md#the-python-environments-window). En outre, si une version de Python plus récente que celle qui apparaît dans le programme d’installation est disponible, vous pouvez installer cette nouvelle version séparément ; Visual Studio la détectera. |
    | **Prise en charge des modèles Cookiecutter** | Installe l’interface utilisateur graphique Cookiecutter pour découvrir des modèles, entrer des options de modèle et créer des projets et fichiers. Consultez [Utiliser l’extension Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Prise en charge de Python web** | Installe des outils pour le développement web incluant la prise en charge de l’édition de code HTML, CSS et JavaScript, ainsi que des modèles pour des projets utilisant les frameworks Bottle, Flask et Django. Consultez [Modèles de projet web Python](python-web-application-project-templates.md). |
    | **Outils de développement natifs Python** | Installe le compilateur C++ et d’autres composants nécessaires pour développer des extensions natives pour Python. Consultez [Créer une extension C++ pour Python](working-with-c-cpp-python-in-visual-studio.md). Installez également la charge de travail **Développement bureautique avec C++** pour bénéficier d’une prise en charge complète. |
    ::: moniker-end

1. Après l’installation, le programme d’installation fournit des options pour modifier, lancer, réparer ou désinstaller Visual Studio. Le bouton **Modifier** se transforme en **Mettre à jour** quand des mises à jour de Visual Studio sont disponibles pour les composants installés. (L’option **modifier** est ensuite disponible dans le menu déroulant.) Vous pouvez également lancer Visual Studio et le programme d’installation à partir du menu **Démarrer** de Windows en effectuant une recherche sur « Visual Studio ».

    ![Lancement, modification ou désinstallation de Visual Studio à partir du programme d’installation](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Dépannage

Si vous rencontrez des problèmes lors de l’installation ou de l’exécution de Python dans Visual Studio, essayez ce qui suit :

- Déterminez si la même erreur se produit avec l’interface CLI Python, autrement dit en exécutant *python.exe* à partir d’une invite de commandes.
- Utilisez l’option [**réparer**](../install/repair-visual-studio.md) dans le programme d’installation de Visual Studio.
- Réparez ou réinstallez python via les **paramètres**  >  **applications & les fonctionnalités** de Windows.

**Exemple d’erreur** : Échec de démarrage du processus interactif : System.ComponentModel.Win32Exception (0x80004005) : Erreur inconnue (0xc0000135) sur Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Exécutez le programme d’installation de Visual Studio en sélectionnant **Panneau de configuration > Programmes et fonctionnalités**, **Microsoft Visual Studio 2015**, puis **Modifier**.

1. Dans le programme d’installation, sélectionnez **Modifier**.

1. Sélectionnez **langages de programmation**  >  **python Tools pour Visual Studio** puis **suivant**:

    ![Option PTVS du programme d’installation de Visual Studio 2015](media/installation-vs2015.png)

1. Une fois l’installation de Visual Studio terminée, [installez un interpréteur Python de votre choix](installing-python-interpreters.md). Visual Studio 2015 ne prend en charge que Python 3.5 et les versions antérieures ; les versions ultérieures génèrent un message du type **Python version 3.6 non pris en charge**). Si vous disposez déjà d’un interpréteur et que Visual Studio ne le détecte pas automatiquement, consultez [Identifier manuellement un environnement existant](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 et versions antérieures

1. Installez la version de Python Tools pour Visual Studio adaptée à votre version de Visual Studio :

    - Visual Studio 2013 : [PTVS 2.2.2 pour Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2). La   >  boîte de dialogue fichier **nouveau projet** de Visual Studio 2013 vous donne un raccourci pour ce processus.
    - Visual Studio 2010 et 2012 : [PTVS 2.1.1 pour Visual studio 2010 et 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Installez un interpréteur Python de votre choix](installing-python-interpreters.md). Si vous disposez déjà d’un interpréteur et que Visual Studio ne le détecte pas automatiquement, consultez [Identifier manuellement un environnement existant](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Emplacements d’installation

Par défaut, la prise en charge de Python est installée pour tous les utilisateurs d’un ordinateur.

Pour Visual Studio 2019 et Visual Studio 2017, la charge de travail Python est installée dans *%ProgramFiles(x86)%\Microsoft Visual Studio\\<VS_version>\\<VS_edition>Common7\IDE\Extensions\Microsoft\Python* où &lt;VS_version&gt; correspond à 2019 ou 2017 et &lt;VS_edition&gt; correspond à Community, Professional ou Enterprise.

Pour Visual Studio 2015 et les versions antérieures, les chemins d’accès de l’installation sont les suivants :

- 32 bits :
  - Chemin d’accès : *% Program Files (x86)% \ Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools pour Visual Studio \\<PTVS_ver>*
  - Emplacement du chemin dans le Registre : **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver>\InstallDir**
- 64 bits :
  - Chemin d’accès : *% Program Files%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools pour visual studio \\<PTVS_ver>*
  - Emplacement du chemin dans le Registre : **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

où :

- &lt;VS_ver&gt; correspond à :
  - 14.0 pour Visual Studio 2015
  - 12.0 pour Visual Studio 2013
  - 11.0 pour Visual Studio 2012
  - 10.0 pour Visual Studio 2010
- &lt;PTVS_ver &gt; est un numéro de version, tel que 2.2.2, 2.1.1, 2,0, 1,5, 1,1 ou 1,0.

### <a name="user-specific-installations-15-and-earlier"></a>Installations propres à l’utilisateur (1.5 et versions antérieures)

Python Tools pour Visual Studio 1.5 et versions antérieures n’autorisent l’installation que pour l’utilisateur actuel. Dans ce cas, le chemin de l’installation est *%LocalAppData%\Microsoft\VisualStudio\\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>*, où les valeurs &lt;VS_ver&gt; et &lt;PTVS_ver&gt; sont identiques à celles décrites ci-dessus.

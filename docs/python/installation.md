---
title: "Installation pour Python dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: cd1ce1ce47705e5e8b63fb3ef7cc36c401503886
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="installing-python-support-in-visual-studio-on-windows"></a>Installation de la prise en charge de Python dans Visual Studio sur Windows

Pour installer la prise en charge de Python pour Visual Studio, suivez les instructions de la section qui correspond à votre version de Visual Studio :

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 et versions antérieures](#visual-studio-2013-and-earlier)

Pour Visual Studio 2015 et antérieur, vous devez aussi installer séparément un interpréteur Python de votre choix (Python 3.5 et antérieur ; la version 3.6 n’est pas prise en charge). Pour plus d’informations, consultez [Environnements Python](python-environments.md). La même page contient également des instructions pour l’ajout d’un interpréteur Python existant à Visual Studio 2017.

Pour tester rapidement la prise en charge de Python après avoir suivi la procédure d’installation, ouvrez la fenêtre interactive Python en appuyant sur Alt+I et en entrant `2+2`. Si vous n’obtenez pas la sortie `4`, passez en revue la procédure que vous avez suivie.

> [!Tip]
> La charge de travail Python inclut la précieuse extension Cookiecutter qui fournit une interface utilisateur graphique permettant de découvrir les modèles, d’entrer les options de modèle et de créer des projets et des fichiers. Pour plus d’informations, consultez [Utilisation de l’extension Cookiecutter](cookiecutter.md).

> [!Note]
> La prise en charge de Python n’est actuellement pas disponible dans Visual Studio pour Mac, mais elle est disponible sur Mac et Linux via Visual Studio Code. Consultez [Questions et réponses](python-in-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Téléchargez et exécutez la dernière version du programme d’installation de Visual Studio 2017 :

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Installer Visual Studio 2017 Community</a>

    >[!Tip]
    > L’édition Community est destinée aux développeurs individuels, à l’apprentissage en classe, à la recherche académique et au développement open source. Pour les autres utilisations, installez <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Professional</a> ou <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Enterprise</a>.

1. Le programme d’installation vous présente une liste de charges de travail, qui sont des groupes d’options connexes pour des types de développement spécifiques. Pour Python, sélectionnez la charge de travail **Développement Python**.

    ![Charge de travail de développement Python dans le programme d’installation de Visual Studio](media/installation-python-workload.png)

    Facultatif : Si vous travaillez dans le domaine de la science des données, considérez également la charge de travail **Applications de science des données et analytiques**. Cette charge de travail inclut la prise en charge de Python, ainsi que les langages R et F#. Pour plus d’informations, consultez [Charge de travail Applications de science et analyse des données](../rtvs/data-science-workload.md).

    > [!Note]
    > Les charges de travail Python et Science des données sont disponibles seulement avec Visual Studio 2017 version 15.2 et ultérieure.

1. Sur le côté droit du programme d’installation, choisissez d’options si vous le souhaitez. Ignorez cette étape pour accepter les options par défaut.

    ![Options de développement Python dans le programme d’installation de Visual Studio](media/installation-python-options.png)

    | Option | Description | 
    | --- | --- |
    | Distributions Python | Choisissez n’importe quelle combinaison des variantes 32 bits et 64 bits des distributions Python 2, Python 3, Anaconda2 et Anaconda3 avec lesquelles vous prévoyez de travailler. Chacune comprend l’interpréteur, le runtime et les bibliothèques de la distribution. Anaconda est une plateforme de science des données ouverte qui inclut une large gamme de packages. (Vous pouvez revenir au programme d’installation de Visual Studio à tout moment pour ajouter ou supprimer des distributions.) |
    | Prise en charge des modèles Cookiecutter | Installe l’interface utilisateur graphique Cookiecutter pour découvrir des modèles, entrer des options de modèle, et créer des projets et des fichiers. Consultez [Utilisation de l’extension Cookiecutter](cookiecutter.md). |
    | Prise en charge de Python web | Installe des outils pour le développement web incluant la prise en charge de l’édition de code HTML, CSS et JavaScript, ainsi que des modèles pour des projets utilisant les frameworks Bottle, Flask et Django. Consultez [Modèles de projet web Python](template-web.md). |
    | Prise en charge de Python IoT | Prend en charge le développement Windows IoT Core avec Python. |
    | Outils de développement natifs Python | Installe le compilateur C++ et d’autres composants nécessaires pour développer des extensions natives pour Python. Consultez [Création d’une extension C++ pour Python](cpp-and-python.md). |
    | Outils principaux pour Azure Cloud Services | Fournit une prise en charge supplémentaire pour le développement Azure Cloud Services en Python. Voir [Projets de service cloud Azure](template-azure-cloud-service.md). |

1. Après l’installation, le programme d’installation fournit des options pour modifier, lancer, réparer ou désinstaller Visual Studio. Le bouton **Modifier** se transforme en **Mettre à jour** quand des mises à jour de Visual Studio sont disponibles pour les composants installés. (L’option Modifier est alors disponible sur le menu déroulant.) Vous pouvez également lancer Visual Studio et le programme d’installation à partir du menu Démarrer de Windows en effectuant une recherche sur « Visual Studio ».

    ![Lancement, modification ou désinstallation de Visual Studio à partir du programme d’installation](media/installation-vs-launch.png)

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Exécutez le programme d’installation de Visual Studio en sélectionnant **Panneau de configuration > Programmes et fonctionnalités**, **Microsoft Visual Studio 2015**, puis **Modifier**.

1. Dans le programme d’installation, sélectionnez **Modifier**.

1. Sélectionnez **Langages de programmation > Python Tools pour Visual Studio**, puis **Suivant** :

    ![Option PTVS du programme d’installation de Visual Studio 2015](media/installation-vs2015.png)    

1. Une fois l’installation de Visual Studio terminée, [installez un interpréteur Python de votre choix](python-environments.md#selecting-and-installing-python-interpreters). Si un interpréteur est déjà installé, consultez [Création d’un environnement pour un interpréteur existant](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 et versions antérieures

1. Installez la version de Python Tools pour Visual Studio adaptée à votre version de Visual Studio :

    - Visual Studio 2013 : [PTVS 2.2 pour Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). La boîte de dialogue **Fichier > Nouveau projet** de Visual Studio 2013 vous offre un raccourci pour ce processus.
    - Visual Studio 2012 : [PTVS 2.1 pour Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478).
    - Visual Studio 2010 : [PTVS 2.1 pour Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479).

1. [Installez un interpréteur Python de votre choix](python-environments.md#selecting-and-installing-python-interpreters). Si un interpréteur est déjà installé, consultez [Création d’un environnement pour un interpréteur existant](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="install-locations"></a>Emplacements d’installation

Par défaut, la prise en charge de Python est installée pour tous les utilisateurs d’un ordinateur.

Pour Visual Studio 2017, la charge de travail Python est installée dans `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python` où &lt;VS_edition&gt; correspond à Community, Professional ou Enterprise.

Pour Visual Studio 2015 et les versions antérieures, les chemins d’accès de l’installation sont les suivants :

- 32 bits :
  - Chemin d’accès : `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Emplacement du chemin d’accès dans le Registre : `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 bits :
  - Chemin d’accès : `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Emplacement du chemin d’accès dans le Registre :`HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

où :

- &lt;VS_ver&gt; correspond à :    
    - 14.0 pour Visual Studio 2015
    - 12.0 pour Visual Studio 2013
    - 11.0 pour Visual Studio 2012
    - 10.0 pour Visual Studio 2010
- &lt;PTVS_ver&gt; est un numéro de version, tel que 2.2, 2.1, 2.0, 1.5, 1.1 ou 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Installations propres à l’utilisateur (1.5 et versions antérieures)

Python Tools pour Visual Studio 1.5 et antérieur n’autorisent l’installation que pour l’utilisateur actuel. Dans ce cas, le chemin d’accès de l’installation est `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`, où les valeurs &lt;VS_ver&gt; et &lt;PTVS_ver&gt; sont identiques à celles décrites ci-dessus.

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />

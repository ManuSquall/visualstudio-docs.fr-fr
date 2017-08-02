---
title: "Installation pour Python dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce3d3656-7ba2-490d-92df-0bb3e3badf92
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 9cdd87d81f0b0f4748a25c7bb87fb840e246854c
ms.contentlocale: fr-fr
ms.lasthandoff: 05/09/2017

---

# <a name="installing-python-support-in-visual-studio"></a>Installation de la prise en charge de Python dans Visual Studio

Pour installer la prise en charge de Python pour Visual Studio, suivez les instructions de la section qui correspond à votre version de Visual Studio :

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 et versions antérieures](#visual-studio-2013-and-earlier)

Notez que pour Visual Studio 2015 et les versions antérieures, vous devez installer séparément un interpréteur Python de votre choix. Pour plus d’informations, consultez l’article [Environnements Python](python-environments.md).

Pour tester rapidement la prise en charge de Python après avoir suivi la procédure d’installation, ouvrez la fenêtre interactive Python en appuyant sur Alt+I et en entrant `2+2`. Si vous n’obtenez pas la sortie `4`, passez en revue la procédure que vous avez suivie.

> [!Tip]
> La charge de travail Python inclut la précieuse extension Cookiecutter qui fournit une interface utilisateur graphique permettant de découvrir les modèles, d’entrer les options de modèle et de créer des projets et des fichiers. Pour plus d’informations, consultez l’article [Using Cookiecutter](cookiecutter.md) (Utilisation de Cookiecutter).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Installez Visual Studio 2017 à partir de [https://www.visualstudio.com/vs/](https://www.visualstudio.com/vs/).

1. Dans le programme d’installation de Visual Studio, sélectionnez la charge de travail **Web et cloud > Développement Python**.

    ![Charge de travail de développement Python dans le programme d’installation de Visual Studio](~/python/media/installation-python-workload.png)

    > [!Note]
    > Python est également inclus dans la charge de travail **Applications de science et analyse des données**.

1. Sur le côté droit du programme d’installation, sélectionnez les interpréteurs Python et les autres outils associés que vous souhaitez inclure. Par exemple, si vous envisagez de développer des extensions C++ pour Python, ajoutez l’option **Outils de développement natifs Python**.

    ![Options de développement Python dans le programme d’installation de Visual Studio](~/python/media/installation-python-options.png)

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Exécutez le programme d’installation de Visual Studio en sélectionnant **Panneau de configuration > Programmes et fonctionnalités**, **Microsoft Visual Studio 2015**, puis **Modifier**.

1. Dans le programme d’installation, sélectionnez **Modifier**.

1. Sélectionnez **Langages de programmation > Python Tools pour Visual Studio**, puis **Suivant** :

    ![Option PTVS du programme d’installation de Visual Studio 2015](~/python/media/installation-vs2015.png)    

1. Une fois l’installation de Visual Studio terminée, [installez un interpréteur Python de votre choix](python-environments.md#selecting-and-installing-python-interpreters).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 et versions antérieures

1. Installez la version de Python Tools pour Visual Studio adaptée à votre version de Visual Studio :

    - Visual Studio 2013 : [PTVS 2.2 pour Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). La boîte de dialogue **Fichier > Nouveau projet** de Visual Studio 2013 vous offre un raccourci pour ce processus.
    - Visual Studio 2012 : [PTVS 2.1 pour Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478).
    - Visual Studio 2010 : [PTVS 2.1 pour Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479).

1. [Installez un interpréteur Python de votre choix](python-environments.md#selecting-and-installing-python-interpreters).

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


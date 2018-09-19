---
title: Utilisation d’un fichier requirements.txt pour gérer les exigences du package
description: Vous pouvez utiliser un fichier requirements.txt pour gérer les dépendances d’un projet. Si vous recevez un projet contenant un fichier requirements.txt, vous pouvez installer ces dépendances en toute simplicité, en une seule étape.
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 478cb56856a5177f74b92542afadb0c36ac946c2
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548788"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Gérer les packages requis avec requirements.txt

Si vous partagez un projet avec d’autres utilisateurs, à l’aide d’un système de génération, ou si vous envisagez de [le publier sur Microsoft Azure](python-azure-cloud-service-project-template.md), vous devez spécifier les packages externes que le projet requiert. L’approche recommandée consiste à utiliser un [fichier requirements.txt](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) qui contient une liste de commandes pour pip qui installe les versions requises des packages dépendants.

Techniquement, vous pouvez utiliser n’importe quel nom de fichier pour suivre les exigences (à l’aide de `-r <full path to file>` durant l’installation d’un package), mais Visual Studio fournit une prise en charge spécifique pour *requirements.txt* :

- Si vous avez chargé un projet contenant *requirements.txt* et si vous souhaitez installer tous les packages listés dans ce fichier, développez le nœud **Environnements Python** dans **l’Explorateur de solutions**, puis cliquez avec le bouton droit sur un nœud d’environnement et sélectionnez **Installer à partir de requirements.txt** :

    ![Installer à partir de requirements.txt](media/environments-requirements-txt-install.png)

- Si vous avez déjà installé tous les packages nécessaires dans un environnement, cliquez avec le bouton droit sur celui-ci dans l’**Explorateur de solutions**, puis sélectionnez **Générer requirements.txt** pour créer le fichier nécessaire. Si le fichier existe déjà, une invite s’affiche sur le mode de mise à jour :

    ![Options de mise à jour pour requirements.txt](media/environments-requirements-txt-replace.png)

  - **Replace entire file** (Remplacer l’intégralité du fichier) supprime tous les éléments, commentaires et options qui existent.
  - **Actualiser les entrées existantes** détecte les spécifications du package et met à jour les spécificateurs de version pour qu’ils correspondent à la version actuellement installée.
  - **Update and add entries** (Mettre à jour et ajouter des entrées) actualise les spécifications trouvées et ajoute tous les autres packages à la fin du fichier.

Dans la mesure où les fichiers *requirements.txt* sont destinés à figer les exigences d’un environnement, tous les packages installés sont écrits avec des versions précises. L’utilisation de versions précises vous assure une reproduction simple de votre environnement sur un autre ordinateur. Les packages sont inclus même s’ils ont été installés avec une plage de versions, en tant que dépendance d’un autre package, ou avec un programme d’installation autre que pip.

Si un package ne peut pas être installé par pip et s’il apparaît dans un fichier *requirements.txt*, cela entraîne l’échec de l’ensemble de l’installation. Dans ce cas, modifiez manuellement le fichier à exclure de ce package ou utilisez [les options de pip](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) pour faire référence à une version installable du package. Par exemple, vous préférez peut-être utiliser [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) pour compiler une dépendance, et ajouter l’option `--find-links <path>` au fichier *requirements.txt* :

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

### <a name="see-also"></a>Voir aussi

- [Gérer les environnements Python dans Visual Studio](managing-python-environments-in-visual-studio.md)
- [Sélectionner un interpréteur pour un projet](selecting-a-python-environment-for-a-project.md)
- [Chemins de recherche](search-paths.md)
- [Référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)

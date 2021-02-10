---
title: Gérer les dépendances de package avec requirements.txt
description: Fichier requirements.txt contenant les dépendances d’un projet. Si vous recevez un projet contenant un fichier requirements.txt, vous pouvez installer ces dépendances en toute simplicité, en une seule étape.
ms.date: 03/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: f535f9d6ad4aa917cde493dfcfe089896634d706
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948112"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Gérer les packages requis avec requirements.txt

Si vous partagez un projet avec d’autres utilisateurs, si vous utilisez un système de build ou si vous prévoyez de copier le projet à un autre emplacement dans lequel vous devrez restaurer un environnement, il vous faut spécifier les packages externes nécessaires au projet. L’approche recommandée consiste à utiliser un [fichier requirements.txt](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) qui contient une liste de commandes pour pip qui installe les versions requises des packages dépendants. La commande la plus courante est `pip freeze > requirements.txt`, qui enregistre la liste des packages actuels d’un environnement dans le fichier *requirements.txt*.

Techniquement, vous pouvez utiliser n’importe quel nom de fichier pour suivre les exigences (à l’aide de `-r <full path to file>` durant l’installation d’un package), mais Visual Studio fournit une prise en charge spécifique pour *requirements.txt* :

- Si vous avez chargé un projet contenant *requirements.txt* et si vous souhaitez installer tous les packages listés dans ce fichier, développez le nœud **Environnements Python** dans **l’Explorateur de solutions**, puis cliquez avec le bouton droit sur un nœud d’environnement et sélectionnez **Installer à partir de requirements.txt** :

    ![Installer à partir de requirements.txt](media/environments/environments-requirements-txt-install.png)

- Si vous souhaitez installer les dépendances dans un environnement virtuel, créez et activez tout d’abord cet environnement, puis utilisez la commande **Installer à partir de requirements.txt**. Pour plus d’informations sur la création d’un environnement virtuel, consultez [Utiliser des environnements virtuels](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Si vous avez déjà installé tous les packages nécessaires dans un environnement, cliquez avec le bouton droit sur celui-ci dans l’**Explorateur de solutions**, puis sélectionnez **Générer requirements.txt** pour créer le fichier nécessaire. Si le fichier existe déjà, une invite s’affiche sur le mode de mise à jour :

    ![Options de mise à jour pour requirements.txt](media/environments/environments-requirements-txt-replace.png)

  - **Replace entire file** (Remplacer l’intégralité du fichier) supprime tous les éléments, commentaires et options qui existent.
  - **Actualiser les entrées existantes** détecte les spécifications du package et met à jour les spécificateurs de version pour qu’ils correspondent à la version actuellement installée.
  - **Update and add entries** (Mettre à jour et ajouter des entrées) actualise les spécifications trouvées et ajoute tous les autres packages à la fin du fichier.

Dans la mesure où les fichiers *requirements.txt* sont destinés à figer les exigences d’un environnement, tous les packages installés sont écrits avec des versions précises. L’utilisation de versions précises vous assure une reproduction simple de votre environnement sur un autre ordinateur. Les packages sont inclus même s’ils ont été installés avec une plage de versions, en tant que dépendance d’un autre package, ou avec un programme d’installation autre que pip.

Si un package ne peut pas être installé par pip et s’il apparaît dans un fichier *requirements.txt*, cela entraîne l’échec de l’ensemble de l’installation. Dans ce cas, modifiez manuellement le fichier à exclure de ce package ou utilisez [les options de pip](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) pour faire référence à une version installable du package. Par exemple, vous préférerez peut-être utiliser [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) pour compiler une dépendance et ajouter l' `--find-links <path>` option à votre *requirements.txt*:

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

## <a name="see-also"></a>Voir aussi

- [Gérer les environnements Python dans Visual Studio](managing-python-environments-in-visual-studio.md)
- [Sélectionner un interpréteur pour un projet](selecting-a-python-environment-for-a-project.md)
- [Chemins de recherche](search-paths.md)
- [Informations de référence sur la fenêtre Environnements Python](python-environments-window-tab-reference.md)

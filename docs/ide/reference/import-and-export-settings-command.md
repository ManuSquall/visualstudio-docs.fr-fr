---
title: Importation et exportation de paramètres (commande)
ms.date: 11/21/2018
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 409c0f40adfd374065dedb842965d2d1237bc9a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568826"
---
# <a name="import-and-export-settings-command"></a>Importation et exportation de paramètres (commande)

Importe, exporte ou réinitialise les paramètres Visual Studio.

## <a name="syntax"></a>Syntaxe

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Commutateurs

/export:`filename`

Option facultative. Exporte les paramètres actuels dans le fichier spécifié.

/import:`filename`

Option facultative. Importe les paramètres figurant dans le fichier spécifié.

/reset

Option facultative. Réinitialise les paramètres actuels.

## <a name="remarks"></a>Notes

L’exécution de cette commande sans commutateur ouvre l’Assistant **Importation et exportation de paramètres**. Pour plus d’informations, consultez [Synchroniser vos paramètres](../synchronized-settings-in-visual-studio.md) et [Paramètres d’environnement](../environment-settings.md).

## <a name="example"></a>Exemple

La commande suivante exporte les paramètres actuels dans le fichier `MyFile.vssettings` :

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Voir aussi

- [Paramètres d’environnement](../../ide/environment-settings.md)
- [Synchroniser vos paramètres](../../ide/synchronized-settings-in-visual-studio.md)
- [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)

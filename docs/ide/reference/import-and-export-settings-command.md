---
description: Importe, exporte ou réinitialise les paramètres Visual Studio. extension de fichier vssettings
title: Importation et exportation de paramètres (commande)
ms.date: 05/28/2021
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dba50cf598c3c74f6c9407fbef5d55f938941a11
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687646"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>Commande importer et exporter des paramètres (fichier. vssettings)

Importe, exporte ou réinitialise le fichier de paramètres Visual Studio, `.vssettings` .

Le schéma du fichier est ouvert. Le plus souvent, le schéma suit une structure XML où chaque catégorie est une balise, qui peut elle-même contenir des balises de sous-catégorie. Ces balises de sous-catégorie peuvent contenir des balises de valeur de propriété. Alors que la plupart des packages utilisent la structure commune, tout package dans Visual Studio peut apporter des données XML arbitraires au fichier avec le schéma qu’il choisit.

## <a name="syntax"></a>Syntax

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Commutateurs

/export:`filename`

facultatif. Exporte les paramètres actuels dans le fichier spécifié.

/import:`filename`

facultatif. Importe les paramètres figurant dans le fichier spécifié.

/reset

facultatif. Réinitialise les paramètres actuels.

## <a name="remarks"></a>Remarques

L’exécution de cette commande sans commutateur ouvre l’Assistant **Importation et exportation de paramètres**. Pour plus d’informations, consultez [Synchroniser vos paramètres](../synchronized-settings-in-visual-studio.md) et [Paramètres d’environnement](../environment-settings.md).

## <a name="example"></a>Exemple

La commande suivante exporte les paramètres actuels dans le fichier `MyFile.vssettings` :

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```



## <a name="see-also"></a>Voir aussi

- [Paramètres d'environnement](../../ide/environment-settings.md)
- [Synchroniser vos paramètres](../../ide/synchronized-settings-in-visual-studio.md)
- [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)

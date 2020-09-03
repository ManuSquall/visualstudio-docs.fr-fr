---
title: Importation et exportation de paramètres (commande) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e3ee8549fd8cf1a4551818c013551ba24128f95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671048"
---
# <a name="import-and-export-settings-command"></a>Importation et exportation de paramètres (commande)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Importe, exporte ou réinitialise les paramètres [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Syntaxe

```
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Commutateurs
 /export:`filename` (facultatif). Exporte les paramètres actuels dans le fichier spécifié.

 /Import : `filename` facultatif. Importe les paramètres figurant dans le fichier spécifié.

 /reset (facultatif). Réinitialise les paramètres actuels.

## <a name="remarks"></a>Notes
 L’exécution de cette commande sans commutateur ouvre l’Assistant **Importation et exportation de paramètres**. Pour plus d’informations, consultez [Guide pratique pour partager des paramètres entre des ordinateurs ou des versions de Visual Studio](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).

## <a name="example"></a>Exemple
 La commande suivante exporte les paramètres actuels dans le fichier `MyFile.vssettings`.

```
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Voir aussi
 [Personnalisation des paramètres de développement dans](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) les [commandes Visual Studio](../../ide/reference/visual-studio-commands.md) Visual Studio

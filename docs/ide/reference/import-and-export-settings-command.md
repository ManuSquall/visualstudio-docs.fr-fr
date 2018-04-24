---
title: Importation et exportation de paramètres (commande) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad7da7f8d83cd45e7cc7801d430dbf70887747b3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="import-and-export-settings-command"></a>Importation et exportation de paramètres (commande)
Importe, exporte ou réinitialise les paramètres [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Commutateurs  
 /export:`filename`  
 Facultative. Exporte les paramètres actuels dans le fichier spécifié.  
  
 /import:`filename`  
 Facultative. Importe les paramètres figurant dans le fichier spécifié.  
  
 /reset  
 Facultative. Réinitialise les paramètres actuels.  
  
## <a name="remarks"></a>Notes

L’exécution de cette commande sans commutateur ouvre l’Assistant **Importation et exportation de paramètres**. Pour plus d’informations, consultez [Synchroniser vos paramètres](../../ide/synchronized-settings-in-visual-studio.md).

## <a name="example"></a>Exemple

La commande suivante exporte les paramètres actuels dans le fichier `MyFile.vssettings`.

```shell
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Voir aussi

[Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)  
[Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
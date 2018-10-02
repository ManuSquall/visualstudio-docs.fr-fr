---
title: Importation et exportation de paramètres (commande) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4a638686bb0ec111bf551cac0b38bb5d50b1774
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495626"
---
# <a name="import-and-export-settings-command"></a>Importation et exportation de paramètres (commande)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [importer et exporter des commandes de paramètres](https://docs.microsoft.com/visualstudio/ide/reference/import-and-export-settings-command).  
  
  
Importe, exporte ou réinitialise les paramètres [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Commutateurs  
 /export:`filename`  
 Facultatif. Exporte les paramètres actuels dans le fichier spécifié.  
  
 /import:`filename`  
 Facultatif. Importe les paramètres figurant dans le fichier spécifié.  
  
 /reset  
 Facultatif. Réinitialise les paramètres actuels.  
  
## <a name="remarks"></a>Notes  
 L’exécution de cette commande sans commutateur ouvre l’Assistant **Importation et exportation de paramètres**. Pour plus d’informations, consultez [Guide pratique pour partager des paramètres entre des ordinateurs ou des versions de Visual Studio](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Exemple  
 La commande suivante exporte les paramètres actuels dans le fichier `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)




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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db7ccd5a4b8266122c2d295cde3cdcca87dc0576
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59657832"
---
# <a name="import-and-export-settings-command"></a>Importation et exportation de paramètres (commande)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Importe, exporte ou réinitialise les paramètres [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Commutateurs  
 /export:`filename`  
 Optionnel. Exporte les paramètres actuels dans le fichier spécifié.  
  
 /import:`filename`  
 Optionnel. Importe les paramètres figurant dans le fichier spécifié.  
  
 /reset  
 Optionnel. Réinitialise les paramètres actuels.  
  
## <a name="remarks"></a>Remarques  
 L’exécution de cette commande sans commutateur ouvre l’Assistant **Importation et exportation de paramètres**. Pour plus d’informations, consultez [Guide pratique pour partager des paramètres entre des ordinateurs ou des versions de Visual Studio](http://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Exemple  
 La commande suivante exporte les paramètres actuels dans le fichier `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)

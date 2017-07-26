---
title: "Importation et exportation de paramètres (commande) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: dca11a81e650f0470c891cb79623f9cc088ea669
ms.contentlocale: fr-fr
ms.lasthandoff: 05/24/2017

---
# <a name="import-and-export-settings-command"></a>Importation et exportation de paramètres (commande)
Importe, exporte ou réinitialise les paramètres [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
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
  
## <a name="remarks"></a>Remarques  
 L’exécution de cette commande sans commutateur ouvre l’Assistant **Importation et exportation de paramètres**. Pour plus d’informations, consultez [Guide pratique pour partager des paramètres entre des ordinateurs ou des versions de Visual Studio](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Exemple  
 La commande suivante exporte les paramètres actuels dans le fichier `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)

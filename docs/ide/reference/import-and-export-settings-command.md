---
title: "Commande Importation et exportation de param&#232;tres | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Tools.ImportandExportSettings"
helpviewer_keywords: 
  - "Tools.ImportandExportSettings"
  - "Importation et exportation de paramètres (commande)"
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Commande Importation et exportation de param&#232;tres
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Importe, exporte ou réinitialise les paramètres [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Syntaxe  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## Commutateurs  
 \/export:`filename`  
 Facultatif.  Exporte les paramètres actuels vers le fichier spécifié.  
  
 \/import:`filename`  
 Facultatif.  Importe les paramètres du fichier spécifié.  
  
 \/reset  
 Facultatif.  Réinitialise les paramètres actuels.  
  
## Notes  
 L'exécution de cette commande sans commutateurs ouvre l'Assistant **Importation et exportation de paramètres**.  Pour plus d'informations, consultez [How to: Share Settings Between Computers or Visual Studio Versions](http://msdn.microsoft.com/fr-fr/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## Exemple  
 La commande suivante exporte les paramètres actuels vers le fichier `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## Voir aussi  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
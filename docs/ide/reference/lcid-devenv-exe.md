---
title: "/LCID (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/l (commutateur de Devenv)"
  - "/lcid (commutateur de Devenv)"
  - "Devenv, /LCID (commutateur)"
  - "langue par défaut"
  - "LCID (commutateur de Devenv)"
  - "ID de paramètres régionaux"
  - "ID de paramètres régionaux, définir des options pour IDE"
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Définit la langue par défaut utilisée pour le texte, la monnaie et d'autres valeurs au sein de l'environnement de développement intégré \(IDE, Integrated Development Environment\).  
  
## Syntaxe  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## Arguments  
 `LocaleID`  
 Obligatoire.  LCID \(ID de paramètres régionaux\) de la langue à spécifier.  
  
## Notes  
 Charge l'IDE et définit le langage naturel par défaut pour l'environnement.  Ce changement est persistant d'une session à une autre et est répercuté dans le volet **Paramètres internationaux** des options **Environnement** de la boîte de dialogue **Options**.  
  
 Si le langage spécifié n'est pas disponible sur le système de l'utilisateur, le commutateur \/LCID est ignoré.  
  
 Le tableau suivant répertorie les LCID des langages pris en charge par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Language|LCID|  
|--------------|----------|  
|Chinois \(Simplifié\)|2052|  
|Chinois \(Traditionnel\)|1028|  
|Anglais|1033|  
|Français|1036|  
|Allemand|1031|  
|Italien|1040|  
|Japonais|1041|  
|Coréen|1042|  
|Espagnol|3082|  
  
## Exemple  
 Cet exemple charge l'IDE avec des chaînes de ressources en anglais.  
  
```  
devenv /LCID 1033  
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Paramètres internationaux, Environnement, boîte de dialogue Options](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Personnalisation des dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md)
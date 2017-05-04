---
title: "Utilisation de fonctionnalit&#233;s Office dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "applications Office (développement Office dans Visual Studio)"
  - "fonctionnalités Office dans Visual Studio"
  - "sécurité (développement Office dans Visual Studio), protection du document"
ms.assetid: 593fd583-57e5-4ed5-8489-89f73b886c6c
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Utilisation de fonctionnalit&#233;s Office dans Visual Studio
  Lorsque vous créez un projet au niveau du document, le document et l'application associée sont hébergés dans Visual Studio, de sorte que vous pouvez concevoir le document et travailler directement avec.  Lorsque qu'une application Microsoft Office est ouverte dans Visual Studio, elle fonctionne généralement comme prévu.  Quelques\-unes des fonctionnalités de l'application sont, toutefois, différentes ou inaccessibles.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Protection de document  
 Microsoft Office Word et Microsoft Office Excel offrent des fonctionnalités de protection de document que vous pouvez utiliser dans vos projets.  Toutefois, si la protection de document est activée pendant que le document est ouvert dans Visual Studio, elle peut vous empêcher d'apporter des modifications à la conception.  Pour plus d’informations, consultez [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md).  
  
## Gestion des droits relatifs à l'information  
 La gestion des droits relatifs à l'information \(IRM\) est disponible dans Microsoft Office Word et Microsoft Office Excel.  IRM peut vous aider à empêcher des personnes non autorisées d'afficher ou de modifier des informations sensibles.  Toutefois, IRM peut également empêcher votre code de s'exécuter.  Pour plus d’informations, consultez [Vue d'ensemble de la gestion des droits relatifs à l'information et des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md).  
  
## Protection par mot de passe  
 Les documents Word Microsoft Office et les classeurs Microsoft Office Excel peuvent être définis de sorte qu'ils ne puissent pas être ouverts par quelqu'un ne connaissant pas le mot de passe.  La protection par mot de passe est contrôlée différemment dans Word et Excel et peut affecter votre processus de développement.  Pour plus d’informations, consultez [Protection par mot de passe des documents Office](../vsto/password-protection-on-office-documents.md).  
  
## Voir aussi  
 [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md)   
 [Vue d'ensemble de la gestion des droits relatifs à l'information et des extensions de code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protection par mot de passe des documents Office](../vsto/password-protection-on-office-documents.md)   
 [Comment : ouvrir des solutions Office sans exécuter le code](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  
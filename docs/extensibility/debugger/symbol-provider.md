---
title: "Fournisseur de symboles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Gestionnaire de symboles"
  - "Gestionnaire de symboles de débogage (débogage SDK),"
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Fournisseur de symboles
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Une implémentation évaluateur d'expression doit accéder aux informations de débogage symboliques générées par le compilateur de langage pour évaluer les variables et des expressions.  Il le fait en consommant interfaces d'un fournisseur de symbole \(SP\), également appelées un gestionnaire de symboles.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit le SPS pour le code managé ainsi que le code natif à l'aide de le format \(PDB\) de fichier de symboles de base de données du programme.  Sauf s'il est nécessaire fort de votre programme d'utiliser des symboles stockés dans un format personnalisé, il est recommandé d'utiliser le SPS fourni par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## remarques d'implémentation  
 Les moteurs de débogage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]comptent parler avec le SPS utilisation d'interfaces \(CLR\) du common langage runtime.  Par conséquent, SP qui doit travailler avec les moteurs de débogage de Visual Studio doit prendre en charge le CLR.  Une liste complète de toutes les interfaces de débogage du CLR peut être récupérée dans debugref.doc, qui fait partie de [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Si votre SP fonctionne uniquement avec votre moteur de débogage personnalisé, vous pouvez implémenter SP lorsque vous consultez l'ajustement selon les besoins de votre moteur de débogage.  
  
## Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)
---
title: "Customizing T4 Text Transformation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, API"
  - "text templates, custom hosts"
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 28
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 28
---
# Customizing T4 Text Transformation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les modèles de texte représentent une fonctionnalité de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui vous permet de générer du code de programme ou d'autres fichiers texte via un processus de transformation.  À l'aide du [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], vous pouvez étendre le processus de transformation de modèle par défaut en personnalisant le processeur de directive de modèle de texte ou l'hôte de modèle de texte.  
  
## Dans cette section  
 [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md)  
 Décrit le mécanisme de transformation de texte et explique le rôle de l'hôte de modèle et des processeurs de directive.  
  
 [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Le processeur de directive traite les directives de votre modèle, telles que `<#@template#>.`. Il s'exécute pendant la compilation du modèle et peut charger des assemblys, ainsi que d'autres ressources.  Il peut également insérer du code qui chargera des ressources au moment de l'exécution.  En définissant votre propre processeur de directive, vous pouvez réduire la complexité de vos modèles.  
  
 [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Si vous écrivez une extension [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] telle qu'une commande de menu ou un gestionnaire d'événements, votre extension peut utiliser le service de création de modèles de texte pour transformer tout modèle de texte.  Vous pouvez passer des données de paramètre dans le modèle à l'aide de l'objet Session et obtenir les valeurs dans le modèle à l'aide de la directive `<#@parameter#>`.  
  
 [Processing Text Templates by using a Custom Host](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Lorsque le code du modèle de texte s'exécute, l'hôte permet l'accès aux fichiers externes et à l'état de l'application.  Par exemple, l'hôte qui exécute les transformations de texte dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] peut permettre l'accès à l'Explorateur de solutions.  Il affiche également les erreurs dans la fenêtre de message d'erreur.  Si vous voulez exécuter des transformations de texte dans un autre contexte, vous pouvez définir votre propre hôte qui permet l'accès aux services disponibles dans ce contexte.  
  
 Si vous écrivez une extension [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], envisagez d'utiliser le service de transformation de texte existant au lieu d'écrire votre propre hôte.  Pour plus d'informations, consultez [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## Référence  
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)  
  
 Fournit la syntaxe des blocs de contrôle et des directives de modèle de texte.
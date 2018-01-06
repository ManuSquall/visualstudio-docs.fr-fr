---
title: "Langage hérité Service Essentials | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3323d317ac8b04731d1573d5c1a05150e012cbfa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-language-service-essentials"></a>Langage hérité Service Essentials
Vous devez fournir un service de langage pour intégrer un langage de programmation Visual Studio. Cette rubrique décrit les fonctionnalités disponibles dans les services de langage hérité.  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
 Les services de langage hérité fournissent les fonctionnalités suivantes :  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Mise en couleur de la syntaxe|Provoque l’affichage de l’éditeur pour afficher les différentes couleurs et styles de police pour différents éléments d’une langue. Cette distinction peut rendre plus facile à lire et modifier des fichiers.<br /><br /> Pour plus d’informations, consultez [coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans managed package framework (MPF), consultez [coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Compléter automatiquement les instructions|Termine une instruction ou le mot clé que l’utilisateur a commencé à taper. Saisie semi-automatique des instructions permet aux utilisateurs d’entrer des instructions difficiles plus facilement, avec moins de risques d’erreur et de taper moins de texte.<br /><br /> Pour plus d’informations, consultez [saisie semi-automatique des instructions dans un Service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, consultez [semi-automatique dans un Service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Accolades correspondantes|Met en évidence couplé caractères tels que les accolades. Lorsque l’utilisateur tape un caractère fermant tels que «} », la correspondance des accolades met en évidence correspondant ouverture caractère, tel que « { ». Lorsqu’il existe plusieurs niveaux de caractères englobants, cette fonctionnalité permet aux utilisateurs pour confirmer que les caractères englobants sont correctement appariées.<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, consultez [accolades correspondantes dans un Service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Info-bulles des informations de paramètre|Affiche la liste des signatures possibles pour la méthode surchargée actuellement la saisie.<br /><br /> Pour plus d’informations, consultez [informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, consultez [informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Marques d’erreur|Affiche un soulignement ondulé rouge, également appelé un ondulées, sous le texte qui a une syntaxe incorrect. Marqueurs d’erreur sont généralement utilisées pour informer les utilisateurs de mots clés mal orthographiés, parenthèses non fermées, caractères non valides et des erreurs similaires.<br /><br /> Dans les classes MPF, les marqueurs d’erreur sont gérées automatiquement dans le <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> méthode de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe.|  
  
 La plupart de ces fonctionnalités requièrent le service de langage pour analyser le code source. Vous pouvez souvent réutiliser les jetons et l’analyse du code pour votre compilateur ou l’interpréteur.  
  
 Les fonctionnalités suivantes sont liées à la prise en charge des langages de programmation, mais ne font pas partie des services de langage :  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Évaluateurs d’expression|Prend en charge la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueur en validant les points d’arrêt et en fournissant une liste d’expressions à afficher dans le **automatique** fenêtre de débogage.<br /><br /> Pour plus d’informations, consultez [prise en charge du Service de langage pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Outils de consultation du symbole|Prend en charge **Explorateur d’objets**, **affichage de classes**, **Explorateur d’appels**, et **rechercher les résultats de symbole**.|
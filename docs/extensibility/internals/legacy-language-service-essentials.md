---
title: Fondamentaux du Service de langage ancien | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f6f8ba46289e27b2465436a103091983c17de1c0
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-essentials"></a>Fondamentaux du Service de langage ancien
Vous devez fournir un service de langage pour intégrer un langage de programmation dans Visual Studio. Cette rubrique décrit les fonctionnalités disponibles dans les services de langage hérité.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
 Les services de langage ancien fournissent les fonctionnalités suivantes :  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Mise en couleur de la syntaxe|Provoque l’affichage de l’éditeur pour afficher les différentes couleurs et styles de police pour différents éléments d’un langage. Cette distinction peut rendre plus facile à lire et modifier des fichiers.<br /><br /> Pour plus d’informations, consultez [la coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans l’infrastructure du package managé (MPF), consultez [coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Compléter automatiquement les instructions|Termine une instruction ou un mot clé que l’utilisateur a commencé à taper. Saisie semi-automatique permet aux utilisateurs d’entrer des instructions difficiles plus facilement, avec moins de frappe et moins de risques d’erreur.<br /><br /> Pour plus d’informations, consultez [saisie semi-automatique des instructions dans un Service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le chargeur multifonctions, consultez [semi-automatique dans un Service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Accolades correspondantes|Points importants associés de caractères tels que les accolades. Lorsque l’utilisateur tape un caractère fermant tels que «} », accolades correspondantes met en évidence correspondants ouvrant caractère, tel que « { ». Lorsqu’il existe plusieurs niveaux de caractères englobants, cette fonctionnalité permet aux utilisateurs pour confirmer que les caractères englobants sont correctement appariées.<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le chargeur multifonctions, consultez [accolades correspondantes dans un Service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Info-bulles d’informations de paramètre|Affiche une liste de signatures possibles de la méthode surchargée actuellement la saisie.<br /><br /> Pour plus d’informations, consultez [informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le chargeur multifonctions, consultez [informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Marqueurs d’erreur|Affiche un soulignement ondulé rouge, également appelé un soulignement ondulé, sous le texte qui est syntaxiquement incorrect. Marqueurs d’erreur sont généralement utilisés pour informer les utilisateurs des mots clés mal orthographiés, parenthèses non fermées, les caractères non valides et des erreurs similaires.<br /><br /> Dans les classes MPF, les marqueurs d’erreur sont gérées automatiquement dans la <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>méthode de la <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe.</xref:Microsoft.VisualStudio.Package.AuthoringSink> </xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>|  
  
 La plupart de ces fonctionnalités requièrent le service de langage pour analyser le code source. Vous pouvez souvent réutiliser les jetons et l’analyse du code pour le compilateur ou l’interpréteur.  
  
 Les fonctionnalités suivantes sont liées à la prise en charge des langages de programmation mais ne font pas partie des services de langage :  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Évaluateurs d’expression|Prend en charge les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueur en validant les points d’arrêt et en fournissant une liste d’expressions à afficher dans le **automatique** fenêtre de débogage.<br /><br /> Pour plus d’informations, consultez [prise en charge du Service de langage pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Outils de consultation du symbole|Prend en charge **Explorateur d’objets**, **affichage de classes**, **Explorateur d’appels**, et **rechercher les résultats des symboles**.|

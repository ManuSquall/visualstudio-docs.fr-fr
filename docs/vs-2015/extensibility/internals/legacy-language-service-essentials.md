---
title: Éléments fondamentaux du Service de langage ancien | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a3926ff84f3b2e6415df1ca7333409c05d839685
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436266"
---
# <a name="legacy-language-service-essentials"></a>Éléments fondamentaux du service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous devez fournir un service de langage pour intégrer un langage de programmation dans Visual Studio. Cette rubrique décrit les fonctionnalités disponibles dans les services de langage hérité.  
  
 Services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
 Services de langage hérité fournissent les fonctionnalités suivantes :  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Mise en couleur de la syntaxe|Provoque l’affichage de l’éditeur pour afficher les différentes couleurs et styles de police pour différents éléments d’un langage. Cette distinction peut rendre plus facile à lire et modifier des fichiers.<br /><br /> Pour obtenir des informations générales, consultez [la coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans l’infrastructure de package managé (MPF), consultez [couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Compléter automatiquement les instructions|Termine une instruction ou le mot clé que l’utilisateur a commencé à taper. Saisie semi-automatique des instructions permet aux utilisateurs d’entrer des instructions difficile plus facilement, avec moins de frappe et moins de risques d’erreur.<br /><br /> Pour obtenir des informations générales, consultez [saisie semi-automatique des instructions dans un Service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, consultez [semi-automatique dans un Service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Accolades correspondantes|Points importants des caractères appariés telles que des accolades. Lorsque l’utilisateur tape un caractère fermant tel que «} », correspondance d’accolade met en évidence le correspondantes ouverture caractère, tel que « { ». Lorsqu’il existe plusieurs niveaux de caractères englobants, cette fonctionnalité aide les utilisateurs à confirmer que les caractères englobants sont correctement appariées.<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, consultez [accolades correspondantes dans un Service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Info-bulles d’informations de paramètre|Affiche une liste de signatures que possible pour la méthode surchargée qui l’actuellement saisie utilisateur.<br /><br /> Pour obtenir des informations générales, consultez [informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, consultez [informations sur les paramètres dans un Service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Marqueurs d’erreur|Affiche un soulignement ondulé rouge, également appelé une ligne ondulé, sous le texte qui a une syntaxe incorrect. Marqueurs d’erreur sont généralement utilisés pour informer les utilisateurs de mots clés mal orthographiés, des parenthèses non fermés, des caractères non valides et des erreurs similaires.<br /><br /> Dans les classes MPF, les marqueurs d’erreur sont gérées automatiquement dans le <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> méthode de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe.|  
  
 La plupart de ces fonctionnalités requièrent le service de langage pour analyser le code source. Vous pouvez souvent réutiliser les jetons et l’analyse du code pour votre compilateur ou l’interpréteur.  
  
 Les fonctionnalités suivantes sont liées à la prise en charge des langages de programmation mais ne font pas partie des services de langage :  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Évaluateurs d’expression|Prend en charge la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueur en validant les points d’arrêt et en fournissant une liste d’expressions à afficher dans le **automatique** fenêtre de débogage.<br /><br /> Pour plus d’informations, consultez [prise en charge du Service de langage pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Outils de consultation de symbole|Prend en charge **Explorateur d’objets**, **affichage de classes**, **Explorateur d’appels**, et **symbole résultats de la recherche**.|

---
title: Legacy Language Service Essentials (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 501bccf755293e86e8a9dc23fce125a10c882376
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707425"
---
# <a name="legacy-language-service-essentials"></a>Éléments fondamentaux du service de langage hérité
Vous devez fournir un service linguistique pour intégrer un langage de programmation dans Visual Studio. Ce sujet explique les caractéristiques disponibles dans les services linguistiques hérités.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon de mettre en œuvre un service linguistique, consultez [Editor et Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

 Les services linguistiques hérités fournissent les caractéristiques suivantes :

|Fonctionnalité|Description|
|-------------|-----------------|
|Mise en couleur de la syntaxe|Provoque la vue de l’éditeur à afficher différentes couleurs et styles de police pour les différents éléments d’une langue. Cette différenciation peut faciliter la lecture et l’édition de fichiers.<br /><br /> Pour plus d’informations générales, voir [Syntax Coloring in a Legacy Language Service](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le cadre de paquet géré (MPF), voir [Syntax Colorizing dans un service de langue héritée](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Compléter automatiquement les instructions|Termine une déclaration ou un mot clé que l’utilisateur a commencé à taper. L’achèvement de l’instruction aide les utilisateurs à saisir les déclarations difficiles plus facilement, avec moins de dactylographie et moins de chances d’erreur.<br /><br /> Pour plus d’informations générales, voir [l’achèvement de l’énoncé dans un service de langue héritée](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, voir [Word Completion in a Legacy Language Service](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Correspondance d’accolade|Faits saillants des personnages appariés tels que des accolades. Lorsque l’utilisateur tape un personnage de clôture tel que « ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' Lorsqu’il existe plusieurs niveaux de caractères d’enceinte, cette fonctionnalité aide les utilisateurs à confirmer que les caractères ci-joints sont correctement appariés.<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, voir [Brace Matching in a Legacy Language Service](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Outils d’information sur les paramètres|Affiche une liste de signatures possibles pour la méthode surchargée que l’utilisateur tape actuellement.<br /><br /> Pour plus d’informations générales, voir [Paramètres Info dans un service de langue héritée](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, voir [Paramètres Info dans un service de langue héritée](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Marqueurs d’erreur|Affiche un soulignement rouge ondulé, également connu sous le nom de squiggly, sous le texte qui est syntaxiquement incorrect. Les marqueurs d’erreur sont généralement utilisés pour sensibiliser les utilisateurs aux mots clés mal orthographiés, aux parenthèses non scellées, aux caractères invalides et aux erreurs similaires.<br /><br /> Dans les classes MPF, les marqueurs <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> d’erreur <xref:Microsoft.VisualStudio.Package.AuthoringSink> sont traités automatiquement dans la méthode de la classe.|

 Bon nombre de ces fonctionnalités nécessitent le service linguistique pour analyser le code source. Vous pouvez souvent réutiliser le code de jetons et d’analyse pour votre compilateur ou interprète.

 Les caractéristiques suivantes sont liées au support pour les langages de programmation, mais ne font pas partie des services linguistiques :

| Fonctionnalité | Description |
|-----------------------| - |
| Évaluateurs d’expression | Prend [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en charge le débagé en validant les points d’arrêt et en fournissant une liste d’expressions à afficher dans la fenêtre **Autos** debug.<br /><br /> Pour plus d’informations, voir [Language Service Support for Debugging](../../extensibility/internals/language-service-support-for-debugging.md). |
| Outils de navigation de symbole | Prend en charge **le navigateur d’objets**, **la vue de classe**, le navigateur **d’appel,** et **trouver les résultats de symbole.** |

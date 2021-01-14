---
title: Notions fondamentales du service de langage hérité | Microsoft Docs
description: Découvrez les fonctionnalités essentielles disponibles dans les services de langage hérité qui vous permettent d’intégrer un langage de programmation dans Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ffa21b619ef17be3fa649732a2b6e3bcd700dda6
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205136"
---
# <a name="legacy-language-service-essentials"></a>Éléments fondamentaux du service de langage hérité
Vous devez fournir un service de langage pour intégrer un langage de programmation dans Visual Studio. Cette rubrique explique les fonctionnalités disponibles dans les services de langage hérités.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et extensions du service de langage](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

 Les services de langage hérités offrent les fonctionnalités suivantes :

|Fonctionnalité|Description|
|-------------|-----------------|
|Mise en couleur de la syntaxe|Fait en sorte que l’affichage de l’éditeur affiche des couleurs et des styles de police différents pour les différents éléments d’une langue. Cette différenciation peut faciliter la lecture et la modification des fichiers.<br /><br /> Pour obtenir des informations générales, consultez [coloration de la syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans Managed package Framework (MPF), consultez [colorisation de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|
|Compléter automatiquement les instructions|Termine une instruction ou un mot clé que l’utilisateur a commencé à taper. La saisie semi-automatique des instructions aide les utilisateurs à entrer plus facilement des instructions difficiles, avec moins de frappe et moins de risques d’erreurs.<br /><br /> Pour obtenir des informations générales, consultez [saisie semi-automatique des instructions dans un service de langage hérité](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, consultez [saisie semi-automatique des mots dans un service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|
|Correspondance d’accolade|Met en surbrillance les caractères associés tels que les accolades. Lorsque l’utilisateur tape un caractère de fermeture tel que « } », la correspondance d’accolade met en surbrillance le caractère d’ouverture correspondant, tel que « { ». Lorsqu’il existe plusieurs niveaux de caractères englobants, cette fonctionnalité permet aux utilisateurs de confirmer que les caractères englobants sont correctement appariés.<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, consultez [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|
|Info-bulles d’informations sur les paramètres|Affiche la liste des signatures possibles pour la méthode surchargée actuellement tapée par l’utilisateur.<br /><br /> Pour obtenir des informations générales, consultez informations sur les [paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Pour plus d’informations sur cette fonctionnalité dans le MPF, consultez informations sur les [paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|
|Marqueurs d’erreur|Affiche une ligne ondulée rouge, également appelée trait ondulé, sous le texte dont la syntaxe est incorrecte. Les marqueurs d’erreur sont généralement utilisés pour que les utilisateurs soient informés des mots clés mal orthographiés, des parenthèses non fermées, des caractères non valides et des erreurs similaires.<br /><br /> Dans les classes MPF, les marqueurs d’erreur sont gérés automatiquement dans la <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> méthode de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe.|

 La plupart de ces fonctionnalités nécessitent que le service de langage analyse le code source. Vous pouvez souvent réutiliser le code de création de jetons et d’analyse pour votre compilateur ou votre interpréteur.

 Les fonctionnalités suivantes sont liées à la prise en charge des langages de programmation, mais ne font pas partie des services de langage :

| Fonctionnalité | Description |
|-----------------------| - |
| Évaluateur d’expression | Prend en charge le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueur en validant des points d’arrêt et en fournissant une liste d’expressions à afficher dans la fenêtre de débogage **automatique** .<br /><br /> Pour plus d’informations, consultez [prise en charge du service de langage pour le débogage](../../extensibility/internals/language-service-support-for-debugging.md). |
| Outils de navigation de symboles | Prend en charge l' **Explorateur d’objets**, les **Affichage de classes**, les **Explorateur d’appels** et les résultats de **recherche de symbole**. |

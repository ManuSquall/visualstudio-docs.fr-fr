---
title: Caractéristiques du service linguistique de l’héritage1 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0be7cb4401792b30eac595faf64162dc375dbb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707399"
---
# <a name="legacy-language-service-features"></a>Fonctionnalités du service de langage hérité
Un service linguistique de cadre de paquet géré [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (MPF) peut prendre en charge une ou plusieurs fonctionnalités, telles que la mise en évidence de la syntaxe, IntelliSense et la validation des points d’arrêt. Chaque fonctionnalité peut être implémentée indépendamment des autres, mais toutes nécessitent un analyseur et un scanner, sauf pour la mise en évidence syntaxe, qui ne nécessite qu’un scanner.

## <a name="in-this-section"></a>Dans cette section
- [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Décrit ce qui est nécessaire pour soutenir l’appariement des paires de langues, également connu sous le nom d’appariement d’accolade.

- [Commentaire du code dans un service de langage hérité](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Décrit ce qui est nécessaire pour étayer les commentaires et le non-engagement du code sélectionné.

- [Propriétés de document personnalisé dans un service de langage hérité](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Décrit ce qui est nécessaire pour prendre en charge les propriétés de documents qui sont intégrées dans un fichier source.

- [Mode Plan dans un service de langage hérité](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Décrit ce qui est nécessaire pour appuyer la mise en œuvre des régions cachées.

- [Reformatage du code dans un service de langage hérité](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Décrit ce qui est nécessaire pour appuyer le code de reformatage.

- [Prise en charge des extraits de code dans un service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Décrit ce qui est nécessaire pour prendre en charge les extraits de code, qui sont des segments de code qui sont insérés et peuvent être modifiés.

- [Informations sur les paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Décrit ce qui est nécessaire pour soutenir l’opération IntelliSense Parameter Info pour afficher une signature de méthode au fur et à mesure que la méthode est tapée.

- [Informations rapides dans un service de langage hérité](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Décrit ce qui est nécessaire pour soutenir l’opération IntelliSense Quick Info pour afficher des informations sur un identifiant.

- [Saisie semi-automatique de membre dans un service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Décrit ce qui est nécessaire pour soutenir l’opération d’achèvement des membres IntelliSense pour la sélection d’un membre d’un espace de nom à partir d’une liste.

- [Saisie semi-automatique de mot dans un service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Décrit ce qui est nécessaire pour soutenir l’opération IntelliSense Complete Word pour remplir des mots partiellement tapés.

- [Prise en charge de Fenêtre Automatique dans un service de langage hérité](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Décrit ce qu’un service linguistique peut faire pour soutenir la fenêtre **Autos** pendant que vous débogiez.

- [Prise en charge de la barre de navigation dans un service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Décrit comment utiliser la **barre de navigation** en haut de la vue de l’éditeur pour fournir une navigation rapide à n’importe quel type ou membre dans le fichier indiqué dans cette vue.

- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Décrit ce qui est nécessaire pour prendre en charge la mise en évidence syntaxique du code source.

- [Validation des points d’arrêt dans un service de langage hérité](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Décrit ce qu’un service linguistique peut faire pour soutenir la validation des points d’arrêt à l’extérieur d’un débbugger.

## <a name="related-sections"></a>Sections connexes
- [Scanneur et analyseur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Décrit le analyseur et le scanner qui sont nécessaires pour mettre en œuvre toutes les fonctionnalités d’un service linguistique qui utilise le cadre de paquet géré.

- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Décrit ce qui est nécessaire pour mettre en œuvre un service linguistique en utilisant le MPF.

- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Décrit les étapes qui sont nécessaires pour enregistrer un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]service linguistique basé sur le MPF avec .

- [Using IntelliSense](../../ide/using-intellisense.md)

 Explique comment IntelliSense facilite l’accès des références linguistiques.

- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Fournit des informations sur la façon d’utiliser le cadre de forfait géré (MPF) pour mettre en œuvre un service linguistique complet dans le code géré.

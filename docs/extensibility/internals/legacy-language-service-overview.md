---
title: Aperçu du service linguistique de l’héritage (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed653ec200063e72434fc758c7920e6caabafe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707358"
---
# <a name="legacy-language-service-overview"></a>Présentation du service de langage hérité
Un service linguistique fournit un support [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] d’éditeur qui vous permet de mettre en œuvre certaines fonctionnalités. Les cours de service linguistique du Cadre de paquets gérés (MPF) fournissent un soutien complet pour les fonctionnalités fréquemment utilisées et un soutien partiel pour d’autres fonctionnalités.

## <a name="fully-supported-features-in-the-mpf"></a>Caractéristiques entièrement prises en charge dans le MPF
 Les cours de service linguistique MPF prennent en charge les caractéristiques suivantes :

- Mise en surbrillance de la syntaxe

- mode Plan

- Commenter les blocs de code

- Correspondance d’accolade

- Extraits de code

- Propriétés de documents personnalisées

- Informations sur les paramètres IntelliSense

- Informations rapides IntelliSense

- Achèvement du membre IntelliSense

- IntelliSense mot achèvement

## <a name="partially-supported-features-in-the-mpf"></a>Caractéristiques partiellement prises en charge dans le MPF
 Le MPF ne fournit qu’un support partiel pour les fonctionnalités suivantes. Cela signifie que vous devez mettre en œuvre les méthodes qui sont appelées par le MPF.

- Code de reformatation. Vous fournissez le code qui implémente la reformatage.

- Valider les points d’arrêt en identifiant les travées de code valides. Vous fournissez le code qui identifie les travées de code.

- Soutenir la fenêtre **Debugger Autos** pour afficher les variables. Vous fournissez le code qui détermine ce qu’il faut afficher dans la fenêtre.

- Soutenir la **barre de navigation** pour une navigation rapide entre les types et les membres. Vous implémentez et retournez une classe d’aide qui remplit les listes dans les boîtes combo **de barre de navigation.**

## <a name="implementation"></a>Implémentation
 Vous devez effectuer plusieurs étapes pour mettre en œuvre le service linguistique lui-même et les fonctionnalités de service linguistique que vous souhaitez prendre en charge pour votre langue. Ces étapes sont discutées dans les sujets suivants :

- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [Mode Plan dans un service de langage hérité](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [Commentaire du code dans un service de langage hérité](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [Reformatage du code dans un service de langage hérité](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [Propriétés de document personnalisé dans un service de langage hérité](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [Prise en charge des extraits de code dans un service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [Prise en charge de la barre de navigation dans un service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Saisie semi-automatique de mot dans un service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Saisie semi-automatique de membre dans un service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Informations sur les paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [Informations rapides dans un service de langage hérité](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Prise en charge de Fenêtre Automatique dans un service de langage hérité](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Validation des points d’arrêt dans un service de langage hérité](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>Voir aussi
- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Extensibilité du service de langage hérité](../../extensibility/internals/legacy-language-service-extensibility.md)

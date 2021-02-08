---
title: Service de langage hérité Features1 | Microsoft Docs
description: En savoir plus sur les fonctionnalités de Visual Studio prises en charge dans un service de langage Managed package Framework (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d34ce48d9543107831ec358a9cf7eeed74d2787b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839662"
---
# <a name="legacy-language-service-features-1"></a>Fonctionnalités du service de langage hérité 1
Un service de langage MPF (Managed package Framework) peut prendre en charge une ou plusieurs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fonctionnalités, telles que la mise en surbrillance syntaxique, IntelliSense et la validation de point d’arrêt. Chaque fonctionnalité peut être implémentée indépendamment des autres, mais tous requièrent un analyseur et un scanneur, à l’exception de la mise en surbrillance syntaxique, qui requiert uniquement un scanneur.

## <a name="in-this-section"></a>Dans cette section
- [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Décrit ce qui est requis pour prendre en charge la correspondance de paires de langues, également appelée correspondance d’accolades.

- [Commentaire du code dans un service de langage hérité](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Décrit ce qui est requis pour prendre en charge les commentaires et supprimer les marques de commentaire du code sélectionné.

- [Propriétés de document personnalisé dans un service de langage hérité](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Décrit ce qui est requis pour prendre en charge les propriétés de document incorporées dans un fichier source.

- [Mode Plan dans un service de langage hérité](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Décrit ce qui est requis pour prendre en charge le mode plan à l’aide de l’implémentation de zones masquées.

- [Reformatage du code dans un service de langage hérité](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Décrit ce qui est requis pour prendre en charge le reformatage du code.

- [Prise en charge des extraits de code dans un service de langage hérité](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Décrit ce qui est requis pour prendre en charge les extraits de code, qui sont des segments de code qui sont insérés et qui peuvent être modifiés.

- [Informations sur les paramètres dans un service de langage hérité](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Décrit ce qui est requis pour prendre en charge l’opération informations sur les paramètres IntelliSense pour afficher une signature de méthode lorsque la méthode est tapée.

- [Informations rapides dans un service de langage hérité](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Décrit ce qui est requis pour prendre en charge l’opération Info Express IntelliSense pour afficher des informations sur un identificateur.

- [Saisie semi-automatique de membre dans un service de langage hérité](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Décrit ce qui est requis pour prendre en charge l’opération d’achèvement de membre IntelliSense pour la sélection d’un membre d’un espace de noms dans une liste.

- [Saisie semi-automatique de mot dans un service de langage hérité](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Décrit ce qui est requis pour prendre en charge l’opération compléter le mot IntelliSense pour l’exécution de mots partiellement typés.

- [Prise en charge de Fenêtre Automatique dans un service de langage hérité](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Décrit ce qu’un service de langage peut effectuer pour prendre en charge la fenêtre **automatique** pendant le débogage.

- [Prise en charge de la barre de navigation dans un service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Décrit comment utiliser la **barre de navigation** en haut de la vue de l’éditeur pour permettre une navigation rapide vers n’importe quel type ou membre du fichier affiché dans cette vue.

- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Décrit ce qui est requis pour prendre en charge la mise en surbrillance syntaxique du code source.

- [Validation des points d’arrêt dans un service de langage hérité](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Décrit ce qu’un service de langage peut effectuer pour prendre en charge la validation de points d’arrêt en dehors d’un débogueur.

## <a name="related-sections"></a>Sections connexes
- [Scanneur et analyseur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Décrit l’analyseur et le scanneur requis pour implémenter toutes les fonctionnalités d’un service de langage qui utilise l’infrastructure de package gérée.

- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Décrit ce qui est requis pour implémenter un service de langage à l’aide du MPF.

- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Décrit les étapes nécessaires pour inscrire un service de langage basé sur MPF avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Utilisation d’IntelliSense](../../ide/using-intellisense.md)

 Explique comment IntelliSense facilite l’accès aux références du langage.

- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Fournit des informations sur l’utilisation de Managed package Framework (MPF) pour implémenter un service de langage complet dans du code managé.

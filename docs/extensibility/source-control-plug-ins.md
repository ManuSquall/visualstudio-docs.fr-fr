---
title: Plug-ins de contrôle des sources (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc5f092e0ae93109d071af0b1a67999947e73e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699891"
---
# <a name="source-control-plug-ins"></a>Plug-ins de contrôle de code source
La section de référence SDK de contrôle source contient la spécification complète [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]de l’interface qui permet d’intégrer les systèmes de contrôle des sources . Il spécifie la syntaxe et la sémantique des différentes fonctions et types [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de données que le plug-in de contrôle source doit mettre en œuvre pour l’interface avec l’environnement de développement intégré (IDE).

## <a name="in-this-section"></a>Dans cette section
- [Fonctions d’API de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md) Répertorie les fonctions qui doivent être implémentées par le plug-in de contrôle source afin de se conformer à l’API de contrôle source.

- [Fonctions de rappel mises en œuvre par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md) Décrit les fonctions que le plug-in de contrôle source utilise pour transmettre des informations à l’IDE pendant que certaines commandes sont exécutées.

- [Enumérateurs](../extensibility/enumerators.md) Répertorie les types de données d’enumérateur dans l’API plug-in source de contrôle que le plug-in de contrôle source doit connaître.

- [Drapeaux de capacité](../extensibility/capability-flags.md) Décrit les `SCC_CAP_xxx` drapeaux, qui indiquent les capacités d’un fournisseur.

- [Bitflags utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) Répertorie les drapeaux utiles dans le contexte de commandes particulières.

- [Codes d’erreur](../extensibility/error-codes.md) Répertorie les valeurs `SCCTRN`d’erreur courantes retournées par les fonctions comme .

- [Cordes utilisées comme clés pour trouver un plug-in de contrôle de source](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Décrit les clés pour accéder au registre pour trouver le plug-in de contrôle source.

- [MSSCCPRJ. SCC File](../extensibility/mssccprj-scc-file.md) décrit un fichier côté client qui contient des informations opaques à l’IDE, mais qui est utilisé par le plug-in de contrôle source pour localiser la solution ou le projet dans le contrôle de la version.

- [Meilleures pratiques pour la mise en œuvre d’un plug-in de contrôle des sources](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Fournit une collection de rappels techniques importants à retenir pendant que vous implémentez l’API rechargeable de contrôle source.

- [Restrictions sur les longueurs des cordes](../extensibility/restrictions-on-string-lengths.md) Décrit les limites de l’API de contrôle source plug-in sur les longueurs des cordes utilisées dans diverses fonctions.

- [Glossaire](../extensibility/source-control-plug-in-glossary.md) Fournit des termes utiles et leurs définitions pour lire la documentation SDK de contrôle source.

- [Comment : Désactiver les avertissements de compatibilité pour les plug-ins de contrôle des sources](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Décrit comment désactiver les avertissements.

## <a name="related-sections"></a>Sections connexes
- [Échantillon de plug-in de contrôle des sources](https://www.microsoft.com/download/details.aspx?id=55984) Fournit un échantillon de fonctionnalité de plug-in de contrôle de source.

- [Guide de test pour les plug-ins de contrôle des sources](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Décrit les procédures d’essai liées à un plug-in de contrôle source.

- [Création d’un plug-in source de contrôle](../extensibility/internals/creating-a-source-control-plug-in.md) Discute de la façon de créer un plug-in de contrôle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] source qui fournit la fonctionnalité de contrôle des sources pendant que vous utilisez l’interface utilisateur de contrôle source (interface utilisateur).

- [Référence Studio visuel SDK](../extensibility/visual-studio-sdk-reference.md) Présente une liste de sujets de référence.

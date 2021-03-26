---
title: Plug-ins de contrôle de code source | Microsoft Docs
description: Les Articles de cette section décrivent la spécification complète de l’interface qui permet d’intégrer les systèmes de contrôle de code source à Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a6788d738d37ac62156958acb15c1bcd5d536515
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089951"
---
# <a name="source-control-plug-ins"></a>Plug-ins de contrôle de code source
La section Référence du kit de développement logiciel (SDK) du plug-in de contrôle de code source contient la spécification d’interface complète qui permet l’intégration des systèmes de contrôle de code source [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Il spécifie la syntaxe et la sémantique des différentes fonctions et types de données que le plug-in de contrôle de code source doit implémenter pour interagir avec l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE).

## <a name="in-this-section"></a>Dans cette section
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md) Répertorie les fonctions qui doivent être implémentées par le plug-in de contrôle de code source afin de se conformer à l’API de plug-in de contrôle de code source.

- [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md) Décrit les fonctions que le plug-in de contrôle de code source utilise pour renvoyer des informations à l’IDE pendant l’exécution de certaines commandes.

- [Énumérateurs](../extensibility/enumerators.md) Répertorie les types de données d’énumérateur dans l’API de plug-in de contrôle de code source que le plug-in de contrôle de code source doit connaître.

- [Indicateurs de capacité](../extensibility/capability-flags.md) Décrit les `SCC_CAP_xxx` indicateurs, qui indiquent les fonctionnalités d’un fournisseur.

- [Indicateurs utilisé par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) Répertorie les indicateurs qui sont utiles dans le contexte de commandes particulières.

- [Codes d’erreur](../extensibility/error-codes.md) Répertorie les valeurs d’erreur courantes retournées par les fonctions en tant que `SCCTRN` .

- [Chaînes utilisées comme clés pour la recherche d’un plug-in de contrôle de code source](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Décrit les clés permettant d’accéder au registre pour rechercher le plug-in de contrôle de code source.

- [Mssccprj. Fichier SCC](../extensibility/mssccprj-scc-file.md) décrit un fichier côté client qui contient des informations opaques pour l’IDE, mais qui est utilisé par le plug-in de contrôle de code source pour localiser la solution ou le projet dans le contrôle de version.

- [Meilleures pratiques pour l’implémentation d’un plug-in de contrôle de code source](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Fournit une collection de rappels techniques importants à retenir lors de l’implémentation de l’API de plug-in de contrôle de code source.

- [Restrictions sur les longueurs de chaîne](../extensibility/restrictions-on-string-lengths.md) Décrit les limitations de l’API de plug-in de contrôle de code source sur les longueurs de chaînes utilisées dans différentes fonctions.

- [Glossaire](../extensibility/source-control-plug-in-glossary.md) Fournit des termes utiles et leurs définitions pour lire la documentation du kit de développement logiciel (SDK) du plug-in de contrôle de code source.

- [Comment : désactiver les avertissements de compatibilité pour les plug-ins de contrôle de code source](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Décrit comment désactiver les avertissements.

## <a name="related-sections"></a>Sections connexes
- [Exemple de plug-in de contrôle de code source](https://www.microsoft.com/download/details.aspx?id=55984) Fournit un exemple de fonctionnalité de plug-in de contrôle de code source.

- [Guide de test pour les plug-ins de contrôle de code source](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Décrit les procédures de test associées à un plug-in de contrôle de code source.

- [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md) Explique comment créer un plug-in de contrôle de code source qui fournit des fonctionnalités de contrôle de code source lorsque vous utilisez l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interface utilisateur du contrôle de code source.

- [Référence du kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk-reference.md) Présente une liste de rubriques de référence.

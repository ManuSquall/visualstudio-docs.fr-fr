---
title: Plug-ins de contrôle de source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a717fdb885669ae4893dc4234c58233dec2957be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62800137"
---
# <a name="source-control-plug-ins"></a>Plug-ins de contrôle de code source
La section de référence du SDK de plug-in de contrôle de code Source contient la spécification de l’interface complète qui permet aux systèmes de contrôle de source être intégré à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Il spécifie la syntaxe et la sémantique des différents types de données et des fonctions que le plug-in de contrôle de code source doit implémenter pour interagir avec le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE).

## <a name="in-this-section"></a>Dans cette section
- [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md) répertorie les fonctions qui doivent être implémentées par le plug-in de contrôle de code source pour vous conformer à l’API de plug-in de contrôle de Source.

- [Les fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md) décrit les fonctions que le plug-in de contrôle de code source utilise pour passer les informations à l’IDE pendant l’exécution de certaines commandes.

- [Énumérateurs](../extensibility/enumerators.md) répertorie les types de données d’énumérateur dans l’API de plug-in de contrôle de Source que le plug-in de contrôle de code source doit connaître.

- [Indicateurs de capacité](../extensibility/capability-flags.md) décrit le `SCC_CAP_xxx` indicateurs, qui sont d’indiquer les fonctionnalités d’un fournisseur.

- [Indicateurs de bits utilisés par les commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md) répertorie les indicateurs qui sont utiles dans le contexte des commandes spécifiques.

- [Codes d’erreur](../extensibility/error-codes.md) répertorie les valeurs d’erreur courantes renvoyées par les fonctions en tant que `SCCTRN`.

- [Chaînes utilisées comme clés pour rechercher un plug-in de contrôle de Source](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) décrit les clés d’accès au Registre pour rechercher le contrôle de source de plug-in.

- [MSSCCPRJ. Fichier de SCC](../extensibility/mssccprj-scc-file.md) décrit un fichier côté client qui contient des informations opaques à l’IDE, mais qui est utilisé par le plug-in de contrôle de code source pour rechercher la solution ou le projet dans le contrôle de version.

- [Meilleures pratiques pour implémenter un plug-in de contrôle de Source](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) fournit une collection de rappels techniques importants à retenir lorsque vous implémentez l’API de plug-in de contrôle de Source.

- [Restrictions relatives aux longueurs de chaîne](../extensibility/restrictions-on-string-lengths.md) décrit les limitations de l’API de plug-in de contrôle de Source sur les longueurs des chaînes utilisées dans les différentes fonctions.

- [Glossaire](../extensibility/source-control-plug-in-glossary.md) fournit des termes utiles et leurs définitions pour la lecture de la documentation du SDK de plug-in de contrôle de code Source.

- [Guide pratique pour Activer Off avertissements de compatibilité pour les Plug-ins de contrôle de code Source](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) décrit comment désactiver les avertissements.

## <a name="related-sections"></a>Rubriques connexes
- [Exemple de plug-in de contrôle de source de](https://www.microsoft.com/download/details.aspx?id=55984) fournit un exemple de fonctionnalité de plug-in de contrôle de code source.

- [Guide de test de Plug-ins de contrôle de code Source](../extensibility/internals/test-guide-for-source-control-plug-ins.md) décrit les procédures de test liés à un plug-in de contrôle de code source.

- [Création d’un plug-in de contrôle de Source](../extensibility/internals/creating-a-source-control-plug-in.md) explique comment créer un plug-in de contrôle de code source qui fournit les fonctionnalités de contrôle de code source pendant que vous utilisez le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interface utilisateur du contrôle source (IU).

- [Référence du Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk-reference.md) présente une liste de rubriques de référence.
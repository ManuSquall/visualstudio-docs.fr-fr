---
title: "Plug-ins de contrôle de source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4f05a0b41a46adfee827f9cc1a36ab7bdd44cd0a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-plug-ins"></a>Plug-ins de contrôle de code source
La section de référence du SDK de plug-in de contrôle de Source contient la spécification de l’interface complète qui permet aux systèmes de contrôle de source être intégrés à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Il spécifie la syntaxe et la sémantique parmi les différents types de données et fonctions que le plug-in de contrôle de code source doit implémenter pour interagir avec les [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)  
 Répertorie les fonctions qui doivent être implémentées par le plug-in de contrôle de code source pour vous conformer à l’API de plug-in de contrôle de Source.  
  
 [Fonctions de rappel implémentées par l’l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Décrit les fonctions que le plug-in de contrôle de code source utilise pour passer les informations à l’IDE pendant que certaines commandes sont exécutées.  
  
 [Énumérateurs](../extensibility/enumerators.md)  
 Répertorie les types de données d’énumérateur dans l’API de plug-in de contrôle Source qui doit reconnaître le plug-in de contrôle de code source.  
  
 [Indicateurs de capacité](../extensibility/capability-flags.md)  
 Décrit le `SCC_CAP_xxx` indicateurs, qui sont indiquent les fonctionnalités d’un fournisseur.  
  
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)  
 Répertorie les indicateurs qui sont utiles dans le contexte des commandes spécifiques.  
  
 [Codes d’erreur](../extensibility/error-codes.md)  
 Répertorie les valeurs d’erreur courantes retournées par les fonctions en tant que `SCCTRN`.  
  
 [Chaînes utilisées comme clés pour rechercher un plug-in de contrôle de code source](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Décrit les clés d’accès au Registre pour rechercher les plug-in du contrôle de code source.  
  
 [Fichier MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Décrit un fichier côté client qui contient des informations opaques à l’IDE, mais qui est utilisé par le plug-in de contrôle de code source pour rechercher la solution ou le projet de contrôle de version.  
  
 [Meilleures pratiques pour implémenter un plug-in de contrôle de code source](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Fournit une collection de rappels techniques importants à retenir lorsque vous implémentez l’API de plug-in de contrôle de Source.  
  
 [Restrictions relatives aux longueurs de chaînes](../extensibility/restrictions-on-string-lengths.md)  
 Décrit les limitations de l’API de plug-in de contrôle de Source sur les longueurs des chaînes utilisées dans les diverses fonctions.  
  
 [Glossaire](../extensibility/source-control-plug-in-glossary.md)  
 Fournit des termes utiles et leurs définitions pour la lecture de la documentation du SDK du plug-in de contrôle de Source.  
  
 [Guide pratique pour désactiver les avertissements de compatibilité pour les plug-ins de contrôle de code source](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Décrit comment désactiver les avertissements.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Exemple de plug-in de contrôle de code source](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Fournit un exemple des fonctionnalités de plug-in de contrôle de code source.  
  
 [Guide de test pour les plug-ins de contrôle de code source](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Décrit les procédures de test liés à un plug-in de contrôle de code source.  
  
 [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Explique comment créer un plug-in de contrôle de code source qui fournit les fonctionnalités de contrôle de code source pendant que vous utilisez le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interface utilisateur du contrôle source (IU).  
  
 [Référence du Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk-reference.md)  
 Présente la liste des rubriques de référence.
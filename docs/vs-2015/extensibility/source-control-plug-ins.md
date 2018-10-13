---
title: Plug-ins de contrôle de source | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 636d36ba34f1c02061671d286725cdd80f6463ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291536"
---
# <a name="source-control-plug-ins"></a>Plug-ins de contrôle de code source
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La section de référence du SDK de plug-in de contrôle de code Source contient la spécification de l’interface complète qui permet aux systèmes de contrôle de source être intégré à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Il spécifie la syntaxe et la sémantique des différents types de données et des fonctions que le plug-in de contrôle de code source doit implémenter pour interagir avec le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)  
 Répertorie les fonctions qui doivent être implémentées par le plug-in de contrôle de code source pour vous conformer à l’API de plug-in de contrôle de Source.  
  
 [Fonctions de rappel implémentées par l’l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Décrit les fonctions que le plug-in de contrôle de code source utilise pour passer les informations à l’IDE pendant l’exécution de certaines commandes.  
  
 [Énumérateurs](../extensibility/enumerators.md)  
 Répertorie les types de données d’énumérateur dans l’API de plug-in de contrôle de Source que le plug-in de contrôle de code source doit connaître.  
  
 [Indicateurs de capacité](../extensibility/capability-flags.md)  
 Décrit le `SCC_CAP_xxx` indicateurs, qui sont d’indiquer les fonctionnalités d’un fournisseur.  
  
 [Indicateurs de bits utilisés par des commandes spécifiques](../extensibility/bitflags-used-by-specific-commands.md)  
 Répertorie les indicateurs qui sont utiles dans le contexte des commandes spécifiques.  
  
 [Codes d’erreur](../extensibility/error-codes.md)  
 Répertorie les valeurs d’erreur courantes renvoyées par les fonctions en tant que `SCCTRN`.  
  
 [Chaînes utilisées comme clés pour rechercher un plug-in de contrôle de code source](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Décrit les touches d’accès au Registre pour rechercher le contrôle de source de plug-in.  
  
 [Fichier MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Décrit un fichier côté client qui contient des informations opaques à l’IDE, mais qui est utilisé par le plug-in de contrôle de code source pour rechercher la solution ou le projet dans le contrôle de version.  
  
 [Meilleures pratiques pour implémenter un plug-in de contrôle de code source](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Fournit une collection de rappels techniques importants à retenir lorsque vous implémentez l’API de plug-in de contrôle de Source.  
  
 [Restrictions relatives aux longueurs de chaînes](../extensibility/restrictions-on-string-lengths.md)  
 Décrit les limitations de l’API de plug-in de contrôle de Source sur les longueurs des chaînes utilisées dans les différentes fonctions.  
  
 [Glossaire](../extensibility/source-control-plug-in-glossary.md)  
 Fournit des termes utiles et leurs définitions pour la lecture de la documentation du SDK de plug-in de contrôle de code Source.  
  
 [Guide pratique pour désactiver les avertissements de compatibilité pour les plug-ins de contrôle de code source](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Décrit comment désactiver les avertissements.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Exemple de plug-in de contrôle de code source](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Fournit un exemple de fonctionnalité de plug-in de contrôle de code source.  
  
 [Guide de test pour les plug-ins de contrôle de code source](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Décrit les procédures de test liés à un plug-in de contrôle de code source.  
  
 [Création d’un plug-in de contrôle de code source](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Explique comment créer un plug-in de contrôle de code source qui fournit les fonctionnalités de contrôle de code source pendant que vous utilisez le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interface utilisateur du contrôle source (IU).  
  
 [Référence du Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk-reference.md)  
 Présente une liste de rubriques de référence.


---
title: Vue d’ensemble de l’intégration du contrôle de code source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e2761958cd60721ccf05a14ec54d3e365572ea1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148378"
---
# <a name="source-control-integration-overview"></a>Présentation de l’intégration du contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette section compare les deux façons d’intégrer dans le contrôle de code source de Visual Studio. un plug-in de contrôle de code source et un VSPackage qui fournit une solution de contrôle de code source et met en évidence les nouvelles fonctionnalités de contrôle de code source. Visual Studio permet un basculement manuel entre les VSPackages de contrôle de code source et les plug-ins de contrôle de code source, ainsi que le basculement automatique basé sur une solution.  
  
## <a name="source-control-integration"></a>Intégration du contrôle de code source  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prend en charge deux types d’options d’intégration du contrôle de code source. Dans toutes les versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , vous pouvez toujours intégrer un plug-in basé sur l’API de plug-in de contrôle de code source (précédemment appelée API MSSCCI), qui fournit une fonctionnalité de contrôle de code source de base lors de l’utilisation de l’interface utilisateur du contrôle de code source Visual Studio. Un VSPackage de contrôle de code source, quant à lui, fournit un nouveau [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] chemin d’intégration profond adapté à l’intégration du contrôle de code source qui requiert un haut niveau de sophistication et une autonomie dans son modèle de contrôle de code source.  
  
 ![Vue d'ensemble du contrôle de code source](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Plug-in de contrôle de code source  
 Toutes les versions de Visual Studio prennent en charge la spécification de l’API du plug-in de contrôle de code source version 1,2 en tant que chemin d’intégration. Un implémenteur de plug-in de contrôle de code source écrit une DLL qui implémente les fonctions API de plug-in de contrôle de code source pour l’intégration et l’inscription du contrôle de code source, comme décrit dans [création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md). Dans cette approche, l’environnement de développement intégré (IDE) utilise l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interface utilisateur pour les boîtes de dialogue, telles que archiver, extraire, les pages de propriétés outils/options, les barres d’outils et les glyphes de contrôle de code source. Un respect strict de l’API de plug-in de contrôle de code source assure une intégration facile dans Visual Studio et une expérience sans problème pour l’utilisateur. Cela signifie que le plug-in de contrôle de code source doit implémenter la plupart des fonctions et rappels détaillés dans l’API.  
  
 Pour implémenter un plug-in de contrôle de code source à l’aide de l’API de plug-in de contrôle de code source, procédez comme suit :  
  
1. Créez une DLL qui implémente les fonctions spécifiées dans les [plug-ins de contrôle de code source](../../extensibility/source-control-plug-ins.md).  
  
2. Inscrivez la DLL en créant les entrées de Registre appropriées (décrites dans [Comment : installer un plug-in de contrôle de code source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3. Créer une interface utilisateur d’assistance et afficher quand il vous est demandé par le package de l’adaptateur de contrôle de code source (le composant Visual Studio qui gère les fonctionnalités de contrôle de code source via les plug-ins de contrôle de code source)  
  
   En réponse à une commande de contrôle de code source, l’IDE de Visual Studio présente une interface utilisateur standard pour les opérations de base, puis transmet les informations au plug-in de contrôle de code source via les fonctions définies dans l’API de plug-in de contrôle de code source. Pour les options avancées, le plug-in de contrôle de code source peut être appelé pour présenter sa propre interface utilisateur, par exemple, pour rechercher un projet sous contrôle de code source. Cela signifie que l’utilisateur peut être présenté avec deux styles d’interface utilisateur éventuellement différents lors du traitement du contrôle de code source : l’interface utilisateur que Visual Studio présente et l’interface utilisateur que le plug-in de contrôle de code source présente. Cela est plus perceptible avec les opérations de contrôle de code source avancées.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Inconvénients de l’implémentation d’un plug-in de contrôle de code source  
  
- Pour les fonctionnalités avancées, l’utilisateur peut voir deux styles différents d’interfaces, ce qui se traduit par une éventuelle confusion.  
  
- Le plug-in de contrôle de code source est limité au modèle de contrôle de code source impliqué par l’API de plug-in de contrôle de code source.  
  
- L’API de plug-in de contrôle de code source est peut-être trop restrictive pour certains scénarios de contrôle de code source.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Avantages de l’implémentation d’un plug-in de contrôle de code source  
  
- Visual Studio fournit toute l’interface utilisateur pour toutes les opérations de contrôle de code source de base afin que le plug-in de contrôle de code source ne soit pas obligé d’implémenter une interface utilisateur potentiellement complexe.  
  
- En raison de l’API stricte, le plug-in de contrôle de code source peut facilement interagir avec les programmes de contrôle de code source externe pour fournir des fonctionnalités plus étendues. Visual Studio ne se soucie pas trop de la façon dont la fonctionnalité de contrôle de code source est accomplie, mais uniquement en fonction de l’API de plug-in de contrôle de code source.  
  
- Il est plus facile d’implémenter un plug-in de contrôle de code source qu’un VSPackage de contrôle de code source.  
  
## <a name="source-control-vspackage"></a>VSPackage de contrôle de code source  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] permet une intégration profonde dans Visual Studio avec le contrôle total de la fonctionnalité de contrôle de code source et le remplacement complet de l’interface utilisateur du contrôle de code source fournie par Visual Studio. Un VSPackage de contrôle de code source est inscrit auprès de Visual Studio et fournit des fonctionnalités de contrôle de code source. Bien que plusieurs VSPackages de contrôle de code source puissent être inscrits dans Visual Studio, une seule d’entre elles peut être active à la fois. Un VSPackage de contrôle de code source a un contrôle total sur la fonctionnalité et l’apparence du contrôle de code source dans Visual Studio pendant qu’il est actif. Tous les autres VSPackages de contrôle de code source qui peuvent être inscrits dans le système sont inactifs et n’affichent aucune interface utilisateur.  
  
 L’implémentation d’un VSPackage de contrôle de code source requiert une stratégie « tout ou rien ». Le créateur d’un VSPackage de contrôle de code source doit investir beaucoup d’efforts dans l’implémentation d’un certain nombre d’interfaces de contrôle de code source et de nouveaux éléments d’interface utilisateur (boîtes de dialogue, menus et barres d’outils) pour couvrir l’ensemble des fonctionnalités de contrôle de code source. Pour plus d’informations, consultez [création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md) .  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Inconvénients de l’implémentation d’un VSPackage de contrôle de code source  
  
- Le VSPackage doit implémenter un certain nombre d’interfaces complexes pour s’intégrer correctement à Visual Studio.  
  
- Le VSPackage doit fournir toute l’interface utilisateur requise pour le contrôle de code source ; Visual Studio ne fournit pas d’assistance dans cette zone.  
  
- Un VSPackage de contrôle de code source est étroitement lié à Visual Studio et ne peut pas fonctionner avec des programmes autonomes, ce qui signifie que les fonctionnalités ne peuvent pas être facilement partagées avec une version externe du programme de contrôle de code source.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Avantages de l’implémentation d’un VSPackage de contrôle de code source  
  
- Étant donné que le VSPackage a un contrôle total sur l’interface utilisateur et les fonctionnalités du contrôle de code source, l’utilisateur reçoit une interface transparente pour le contrôle de code source.  
  
- Le VSPackage n’est pas limité à un modèle de contrôle de code source particulier.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de code source](../../extensibility/internals/source-control.md)   
 [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Nouveautés du contrôle de code source](../../extensibility/internals/what-s-new-in-source-control.md)

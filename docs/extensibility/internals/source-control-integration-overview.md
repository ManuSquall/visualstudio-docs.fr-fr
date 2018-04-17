---
title: Vue d’ensemble de l’intégration de contrôle de source | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19d75936e21729729dfeafaa041d800acbe01caa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-integration-overview"></a>Vue d’ensemble de l’intégration de contrôle source
Cette section compare les deux façons d’intégrer le contrôle de code source Visual Studio ; un contrôle de source de plug-in et un VSPackage qui fournit une solution de contrôle de code source et met en évidence les nouvelles fonctionnalités de contrôle de code source. Visual Studio permet un basculement manuel entre le contrôle de code source VSPackages et les plug-ins de contrôle de code source, ainsi que pour le basculement automatique sur les solutions.  
  
## <a name="source-control-integration"></a>Intégration du contrôle de code source  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge deux types d’options d’intégration de contrôle de code source. Dans toutes les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez toujours intégrer un plug-in en fonction de la Source de plug-in API de contrôle (précédemment reflétant l’API MSSCCI), qui fournit des fonctionnalités de contrôle de source de base lors de l’utilisation de Visual Studio source contrôle utilisateur interface ( INTERFACE UTILISATEUR). Un contrôle de code source VSPackage, quant à eux, intègre un nouveau, deep- [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] chemin d’accès approprié pour l’intégration de contrôle de code source qui exige un niveau élevé de sophistication et d’autonomie dans son modèle de contrôle de code source.  
  
 ![Vue d’ensemble du contrôle de source](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Plug-in de contrôle de code source  
 Toutes les versions de Visual Studio prend en charge l’API de plug-in de contrôle de Source de version 1.2 de la spécification comme un chemin d’accès de l’intégration. Un implémenteur de plug-in de contrôle de code source écrit une DLL qui implémente les fonctions API de plug-in de contrôle de code Source pour l’intégration du contrôle source et de l’inscription, comme décrit dans [création d’un plug-in de contrôle de code Source](../../extensibility/internals/creating-a-source-control-plug-in.md). Dans cette approche, l’environnement de développement intégré (IDE) utilise le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur pour les boîtes de dialogue, tel que vérification de l’extraction, les pages de propriétés d’outils/options, les barres d’outils et les glyphes de contrôle de code source. Respect strict à l’API de plug-in du contrôle Source garantit une intégration facile avec Visual Studio et une expérience sans problème pour l’utilisateur. Cela signifie que le plug-in de contrôle de code source doit implémenter la plupart des fonctions et des rappels détaillés dans l’API.  
  
 Pour implémenter un plug-in à l’aide de l’API de plug-in de contrôle de Source de contrôle de code source, procédez comme suit :  
  
1.  Créer une DLL qui implémente les fonctions spécifiées dans [Plug-ins de contrôle de code Source](../../extensibility/source-control-plug-ins.md).  
  
2.  Inscrire la DLL en effectuant les entrées de Registre appropriées (décrit dans [Comment : installer un plug-in de contrôle de code Source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3.  Créer un programme d’assistance de l’interface utilisateur et l’affichage lorsque vous y êtes invité par le Package de l’adaptateur de contrôle de Source (le composant de Visual Studio qui gère les fonctionnalités de contrôle de code source via le plug-ins de contrôle de code source)  
  
 En réponse à une commande de contrôle de code source, l’IDE Visual Studio présente une interface utilisateur standard pour les opérations de base et transmet ensuite les informations de contrôle de source de plug-in via les fonctions définies dans l’API de plug-in de contrôle de Source. Options avancées, le plug-in de contrôle de code source peut être appelé sur pour présenter sa propre interface utilisateur, par exemple, recherche d’un projet sous contrôle de code source. Cela signifie que l’utilisateur peut être présenté avec les deux styles différentes de l’interface utilisateur lors du traitement de contrôle de code source : l’interface utilisateur qui présente de Visual Studio et l’interface utilisateur et présentant le plug-in de contrôle de code source. Il s’agit plus perceptible avec les opérations de contrôle de source avancées.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Inconvénients à l’implémentation d’un plug-in de contrôle de code Source  
  
-   Pour les fonctionnalités avancées, l’utilisateur peut voir deux styles différents des interfaces, ce qui risque de confusion.  
  
-   Le plug-in de contrôle de code source est limité dans le modèle de contrôle de source impliqué par l’API de plug-in de contrôle de Source.  
  
-   L’API de plug-in de contrôle de Source est peut-être trop restrictive pour certains scénarios de contrôle de code source.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Avantages de l’implémentation d’un plug-in de contrôle de code Source  
  
-   Visual Studio fournit l’interface utilisateur pour toutes les opérations de contrôle de source de base afin que le plug-in de contrôle de code source ne dispose pas d’implémenter l’interface utilisateur potentiellement complexe.  
  
-   En raison de l’API strict, le plug-in de contrôle de code source peut facilement interagir avec des programmes de contrôle de source externe pour fournir des fonctionnalités plus étendues ; Visual Studio ne soucie pas trop bien comment la fonctionnalité de contrôle de code source est accomplie, seulement qu’elle s’effectue en fonction de l’API de plug-in de contrôle de Source.  
  
-   Il est plus facile à implémenter un contrôle de source de plug-in à un contrôle de code source VSPackage.  
  
## <a name="source-control-vspackage"></a>VSPackage de contrôle de code source  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] permet une intégration complète dans Visual Studio avec le contrôle total sur les fonctionnalités de contrôle de code source et un remplacement complet de l’interface utilisateur du contrôle source fournis par Visual Studio. Un contrôle de code source VSPackage est enregistrée avec Visual Studio et fournit des fonctionnalités de contrôle de code source. Bien que le contrôle de code source plusieurs VSPackages peut être inscrits avec Visual Studio, un seul d'entre eux peut être active à tout moment. Un VSPackage de contrôle de code source a un contrôle total sur la fonctionnalité de contrôle de code source et l’apparence dans Visual Studio lorsqu’elle est active. Tous les autres contrôle de code source VSPackages qui peut être enregistrés dans le système sont inactif et n’affichera pas d’interface utilisateur du tout.  
  
 Implémentation d’un contrôle de code source VSPackage nécessite une stratégie « tout ou rien ». Le créateur d’un contrôle de code source VSPackage doit investir une quantité importante de l’effort de mise en œuvre d’un nombre d’interfaces de contrôle de code source et de nouveaux éléments d’interface utilisateur (boîtes de dialogue, les menus et barres d’outils) pour couvrir la fonctionnalité de contrôle de source entière. Consultez [création d’un VSPackage de contrôle de Source](../../extensibility/internals/creating-a-source-control-vspackage.md) pour plus d’informations.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Inconvénients à l’implémentation d’un VSPackage de contrôle de code Source  
  
-   Le VSPackage doit implémenter plusieurs interfaces complexes pour intégrer correctement à Visual Studio.  
  
-   Le VSPackage doit fournir l’interface utilisateur requis pour le contrôle de code source ; Visual Studio ne fournit aucune assistance dans cette zone.  
  
-   Un contrôle de code source VSPackage est étroitement lié à Visual Studio et ne peut pas fonctionner avec les programmes autonomes, afin de fonctionnalités ne peut pas être facilement partagées avec une version externe de l’application de contrôle de source.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Avantages de l’implémentation d’un VSPackage de contrôle de code Source  
  
-   Étant donné que le VSPackage possède des fonctionnalités et un contrôle total sur l’interface utilisateur du contrôle de code source, l’utilisateur est présenté avec une interface transparente pour le contrôle de code source.  
  
-   Le package Visual Studio n’est pas limité à un modèle de contrôle de source en question.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de code source](../../extensibility/internals/source-control.md)   
 [Création d’un contrôle de Source de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Création d’un VSPackage de contrôle de code Source](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Nouveautés du contrôle de code source](../../extensibility/internals/what-s-new-in-source-control.md)
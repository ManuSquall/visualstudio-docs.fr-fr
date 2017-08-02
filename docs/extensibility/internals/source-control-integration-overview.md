---
title: "Vue d’ensemble de l’intégration de contrôle de source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d3facc06885ef927448eb506ff2f4aa5c04ce85f
ms.lasthandoff: 02/22/2017

---
# <a name="source-control-integration-overview"></a>Vue d’ensemble de l’intégration de contrôle source
Cette section compare les deux façons d’intégrer le contrôle de code source Visual Studio ; un contrôle de source de plug-in et un VSPackage qui fournit une solution de contrôle de code source et met en évidence les nouvelles fonctionnalités de contrôle de code source. Visual Studio permet le basculement manuel entre le contrôle de source de packages VS et les plug-ins de contrôle de code source ainsi que le basculement automatique sur les solutions.  
  
## <a name="source-control-integration"></a>Intégration du contrôle de code source  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]prend en charge deux types d’options d’intégration de contrôle de code source. Dans toutes les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez toujours intégrer un plug-in basé sur la Source du plug-in API de contrôle (précédemment reflétant l’API MSSCCI), qui fournit la fonctionnalité de contrôle de source de base tout en utilisant l’interface utilisateur (IU) de Visual Studio source contrôle. Un contrôle de code source VSPackage, fournit en revanche, une intégration approfondie nouvelle, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] chemin d’accès approprié pour l’intégration de contrôle de source qui exige un niveau élevé de complexité et d’autonomie dans son modèle de contrôle de code source.  
  
 ![Vue d’ensemble du contrôle de source](~/extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Plug-in de contrôle de code source  
 Toutes les versions de Visual Studio prend en charge l’API de plug-in de contrôle de Source version 1.2 de la spécification comme un chemin d’accès de l’intégration. Un implémenteur de plug-in de contrôle de code source écrit une DLL qui implémente les fonctions API de plug-in de contrôle de code Source pour l’intégration de contrôle de code source et d’enregistrement, comme décrit dans [création d’un plug-in de contrôle de code Source](../../extensibility/internals/creating-a-source-control-plug-in.md). Dans cette approche, l’environnement de développement intégré (IDE) utilise le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur pour les boîtes de dialogue, tels que l’intégration, extraction, les pages de propriétés outils/options, les barres d’outils et les glyphes de contrôle de code source. Respect strict de l’API de plug-in de contrôle de Source garantit une intégration facile avec Visual Studio et une expérience sans problème à l’utilisateur. Cela signifie que le plug-in de contrôle de code source doit implémenter la plupart des fonctions et des rappels détaillés dans l’API.  
  
 Pour implémenter un plug-in à l’aide de l’API de plug-in de contrôle de Source de contrôle de code source, procédez comme suit :  
  
1.  Créer une DLL qui implémente les fonctions spécifiées dans [Plug-ins de contrôle de code Source](../../extensibility/source-control-plug-ins.md).  
  
2.  Inscrire la DLL en ajoutant les entrées de Registre appropriées (décrit dans [Comment : installer un plug-in de contrôle de code Source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3.  Créer une application d’assistance de l’interface utilisateur et l’afficher lorsque vous y êtes invité par le Package de l’adaptateur de contrôle Source (le composant de Visual Studio qui gère les fonctionnalités de contrôle de code source via des plug-ins de contrôle de code source)  
  
 En réponse à une commande de contrôle de code source, l’IDE Visual Studio présente une interface utilisateur standard pour les opérations de base, puis passe les informations du contrôle de code source du plug-in via les fonctions définies dans l’API de plug-in de contrôle de Source. Options avancées, le plug-in de contrôle de code source peut-être être appelé sur pour présenter sa propre interface utilisateur, par exemple, pour un projet de contrôle de code source de navigation. Cela signifie que l’utilisateur peut s’afficher deux styles différents de l’interface utilisateur lors du traitement du contrôle de code source : Visual Studio présente l’interface utilisateur et l’interface utilisateur qui présente le plug-in de contrôle de code source. Cela est particulièrement visible avec les opérations de contrôle de code source avancées.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Inconvénients liés à l’implémentation d’un plug-in de contrôle de code Source  
  
-   Pour les fonctionnalités avancées, l’utilisateur peut voir deux styles d’interfaces, ce qui risque de confusion.  
  
-   Le plug-in de contrôle de code source est limité dans le modèle de contrôle source impliqué par l’API de plug-in de contrôle de Source.  
  
-   L’API de plug-in de contrôle de Source peuvent être trop restrictive pour certains scénarios de contrôle de code source.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Avantages de l’implémentation d’un plug-in de contrôle de code Source  
  
-   Visual Studio fournit l’interface utilisateur de toutes les opérations de contrôle de source de base afin que le plug-in de contrôle de code source n’a pas d’implémenter une interface utilisateur potentiellement complexe.  
  
-   En raison de l’API strict, le plug-in de contrôle de code source peut facilement interagir avec les programmes de contrôle de source externe pour fournir des fonctionnalités plus complètes ; Visual Studio ne préoccupe pas trop bien comment la fonctionnalité de contrôle de code source est accomplie, qu’il s’effectue en fonction de l’API de plug-in de contrôle de Source.  
  
-   Il est plus facile à implémenter un contrôle de source de plug-in à un contrôle de code source VSPackage.  
  
## <a name="source-control-vspackage"></a>VSPackage de contrôle de code source  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]permet une intégration approfondie avec contrôle total sur les fonctionnalités de contrôle de code source et un remplacement complet de l’interface utilisateur du contrôle source fournis par Visual Studio dans Visual Studio. Un contrôle de code source VSPackage est enregistré avec Visual Studio et fournit des fonctionnalités de contrôle de code source. Bien que le contrôle de source de plusieurs packages VS peut être enregistrée avec Visual Studio, un seul d'entre eux peut être active à la fois. Un contrôle de code source VSPackage a un contrôle total sur les fonctionnalités de contrôle de code source et l’apparence dans Visual Studio lorsqu’elle est active. Tous les autres contrôle de code source qui peuvent être enregistrés dans le système de packages VS sont inactif et n’affiche aucune interface utilisateur du tout.  
  
 L’implémentation d’un contrôle de code source VSPackage nécessite une stratégie « tout ou rien ». Le créateur d’un contrôle de code source VSPackage doit investir beaucoup d’efforts dans l’implémentation de plusieurs interfaces de contrôle de source et de nouveaux éléments d’interface utilisateur (boîtes de dialogue, les menus et barres d’outils) pour couvrir la fonctionnalité de contrôle de code source entière. Consultez la page [création d’un contrôle de Source de package VS](../../extensibility/internals/creating-a-source-control-vspackage.md) pour plus de détails.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Inconvénients liés à l’implémentation d’un VSPackage de contrôle de code Source  
  
-   Le VSPackage doit implémenter les interfaces complexes à intégrer correctement avec Visual Studio.  
  
-   Le VSPackage doit fournir l’interface utilisateur requis pour le contrôle de code source ; Visual Studio ne fournira aucune assistance dans cette zone.  
  
-   Un contrôle de code source VSPackage est étroitement lié à Visual Studio et ne peut pas fonctionner avec les programmes autonomes, donc la fonctionnalité ne peut pas être partagée facilement avec une version du programme de contrôle de source externe.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Avantages de l’implémentation d’un VSPackage de contrôle de code Source  
  
-   Le VSPackage ayant des fonctionnalités et un contrôle total sur le contrôle de source de l’interface utilisateur, l’utilisateur est présenté avec une interface transparente pour le contrôle de code source.  
  
-   Le VSPackage n’est pas limité à un modèle de contrôle source particulière.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de code source](../../extensibility/internals/source-control.md)   
 [Création d’un contrôle de Source de plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Création d’un VSPackage de contrôle de code Source](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Nouveautés du contrôle de code Source](../../extensibility/internals/what-s-new-in-source-control.md)

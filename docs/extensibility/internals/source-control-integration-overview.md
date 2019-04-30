---
title: Vue d’ensemble de l’intégration de contrôle de source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4bd2a688e2a10bf0b931851b0d4366684820bf1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62859000"
---
# <a name="source-control-integration-overview"></a>Présentation de l’intégration du contrôle de code source
Cette section compare les deux façons d’intégrer le contrôle de code source Visual Studio ; un contrôle de source de plug-in et un VSPackage qui fournit une solution de contrôle source et met en évidence les nouvelles fonctionnalités de contrôle de code source. Visual Studio permet un basculement manuel entre le contrôle de code source VSPackages et les plug-ins de contrôle de code source, ainsi que pour le basculement automatique basé sur la solution.

## <a name="source-control-integration"></a>Intégration du contrôle de code source
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend en charge deux types d’options d’intégration de contrôle de code source. Dans toutes les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vous pouvez toujours intégrer un plug-in basé sur la Source contrôle plug-in API (précédemment reflétant l’API MSSCCI), qui fournit la fonctionnalité de contrôle de source de base lors de l’utilisation de Visual Studio source contrôle utilisateur interface ( INTERFACE UTILISATEUR). Un contrôle de code source VSPackage, en revanche, s’intègre une nouvelle, deep- [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] chemin d’accès adéquat pour l’intégration du contrôle de code source qui exige un haut niveau de sophistication et autonomie dans son modèle de contrôle de code source.

 ![Vue d’ensemble du contrôle de source](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Plug-in de contrôle de code source
 Toutes les versions de Visual Studio prend en charge l’API de plug-in de contrôle de Source version 1.2 de la spécification comme un chemin d’accès de l’intégration. Un implémenteur de plug-in de contrôle de code source écrit une DLL qui implémente les fonctions API de plug-in de contrôle de code Source pour l’intégration du contrôle de source et de l’inscription, comme décrit dans [création d’un plug-in de contrôle de Source](../../extensibility/internals/creating-a-source-control-plug-in.md). Dans cette approche, l’environnement de développement intégré (IDE) utilise le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur pour les boîtes de dialogue, tel que vérification de l’extraction, les pages de propriétés des outils/options, les barres d’outils et les glyphes de contrôle de code source. Respect strict de l’API de plug-in de contrôle de Source garantit une intégration facile avec Visual Studio et une expérience sans problème pour l’utilisateur. Cela signifie que le plug-in de contrôle de code source doit implémenter la plupart des fonctions et des rappels détaillées dans l’API.

 Pour implémenter un plug-in à l’aide de l’API de plug-in de contrôle de Source de contrôle de code source, procédez comme suit :

1. Créer une DLL qui implémente les fonctions spécifiées dans [Plug-ins de contrôle de code Source](../../extensibility/source-control-plug-ins.md).

2. Inscrivez la DLL en rendant les entrées de Registre appropriées (décrit dans [Comment : Installer un plug-in de contrôle de code Source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).

3. Créer une assistance de l’interface utilisateur et l’affichage lorsque vous y êtes invité par le Package de l’adaptateur de contrôle de code Source (le composant de Visual Studio qui gère les fonctionnalités de contrôle de code source par le biais de plug-ins de contrôle de code source)

   En réponse à une commande de contrôle de code source, l’IDE Visual Studio présente une interface utilisateur standard pour les opérations de base et transmet ensuite les informations pour le contrôle de source de plug-in via les fonctions définies dans l’API de plug-in de contrôle de Source. Pour les options avancées, le plug-in de contrôle de code source peut être appelé sur pour présenter son propre interface utilisateur, par exemple, pour un projet sous contrôle de code source de navigation. Cela signifie que l’utilisateur peut s’afficher avec les deux styles pouvant être différents de l’interface utilisateur lors du traitement de contrôle de code source : l’interface utilisateur qui présente Visual Studio et l’interface utilisateur qui présente le plug-in de contrôle de code source. Il s’agit plus perceptible avec les opérations de contrôle source avancées.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Inconvénients à l’implémentation d’un plug-in de contrôle de code Source

- Pour des fonctionnalités avancées, l’utilisateur peut voir deux styles différents des interfaces, ce qui conduit à un risque de confusion.

- Le plug-in de contrôle de code source est limité dans le modèle de contrôle de source impliqué par l’API de plug-in de contrôle de Source.

- L’API de plug-in de contrôle de Source peuvent être trop restrictive pour certains scénarios de contrôle de code source.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Avantages à implémenter un plug-in de contrôle de code Source

- Visual Studio fournit l’interface utilisateur pour toutes les opérations de contrôle de source de base afin que le plug-in de contrôle de code source n’a pas d’implémenter une interface utilisateur potentiellement complexe.

- En raison de l’API strict, le plug-in de contrôle de code source peut facilement interagir avec les programmes de contrôle de source externe pour fournir des fonctionnalités plus complètes ; Visual Studio ne soucie pas trop bien comment la fonctionnalité de contrôle de code source est accomplie, uniquement qu’elle s’effectue en fonction de l’API de plug-in de contrôle de Source.

- Il est plus facile à implémenter un plug-in à un VSPackage de contrôle de source de contrôle de code source.

## <a name="source-control-vspackage"></a>VSPackage de contrôle de code source
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] permet une intégration approfondie dans Visual Studio avec le contrôle total sur les fonctionnalités de contrôle de code source et un remplacement complet de l’interface utilisateur du contrôle source fourni par Visual Studio. Un contrôle de code source VSPackage est inscrit avec Visual Studio et fournit des fonctionnalités de contrôle de code source. Bien que le contrôle de code source plusieurs VSPackages peut être enregistré avec Visual Studio, un seul d'entre eux peut être actif à tout moment. Un VSPackage de contrôle de code source a un contrôle total sur la fonctionnalité de contrôle de code source et l’apparence dans Visual Studio lorsqu’elle est active. Tous les autres contrôle de code source VSPackages qui peuvent être enregistrés dans le système sont inactifs et n’affichera pas d’interface utilisateur du tout.

 Implémentation d’un VSPackage de contrôle de code source nécessite une stratégie « tout ou rien ». Le créateur d’un VSPackage de contrôle de code source doit investir beaucoup d’efforts dans l’implémentation d’un nombre d’interfaces de contrôle de source et de nouveaux éléments d’interface utilisateur (boîtes de dialogue, les menus et barres d’outils) afin de couvrir les fonctionnalités de contrôle de source entière. Consultez [création d’un VSPackage de contrôle de code Source](../../extensibility/internals/creating-a-source-control-vspackage.md) pour plus d’informations.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Inconvénients à l’implémentation d’un VSPackage de contrôle de code Source

- Le VSPackage doit implémenter les interfaces complexes pour intégrer correctement à Visual Studio.

- Le VSPackage doit fournir l’interface utilisateur requis pour le contrôle de code source ; Visual Studio ne fournissent aucune aide dans cette zone.

- Un contrôle de code source VSPackage est étroitement lié à Visual Studio et ne peut pas fonctionner avec des programmes indépendants, afin de la fonctionnalité ne peut pas être aussi facilement partagée avec une version du programme de contrôle de source externe.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Avantages à l’implémentation d’un VSPackage de contrôle de code Source

- Étant donné que le VSPackage a des fonctionnalités et un contrôle total sur l’interface utilisateur du contrôle de code source, l’utilisateur est présenté avec une interface transparente pour le contrôle de code source.

- Le VSPackage n’est pas limité à un modèle de contrôle de code source particulier.

## <a name="see-also"></a>Voir aussi
- [Contrôle de code source](../../extensibility/internals/source-control.md)
- [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Nouveautés du contrôle de code source](../../extensibility/internals/what-s-new-in-source-control.md)
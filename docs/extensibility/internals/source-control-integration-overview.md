---
title: Aperçu de l’intégration du contrôle des sources (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80363286f5f0cac9a5ceb2e8ac9d20345df9e6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705126"
---
# <a name="source-control-integration-overview"></a>Présentation de l’intégration du contrôle de code source
Cette section compare les deux façons de s’intégrer dans le contrôle des sources Visual Studio; un plug-in de contrôle source et un VSPackage qui fournit une solution de contrôle source et met en évidence les nouvelles fonctionnalités de contrôle source. Visual Studio permet le commutation manuelle entre les VSPackages de contrôle source et les plug-ins de contrôle source ainsi que la commutation automatique basée sur la solution.

## <a name="source-control-integration"></a>Intégration du contrôle de code source
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]prend en charge deux types d’options d’intégration de contrôle des sources. Dans toutes les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]versions de , vous pouvez toujours intégrer un plug-in basé sur l’API de contrôle source plug-in (précédemment également appelé l’API MSSCCI), qui fournit la fonctionnalité de contrôle source de base tout en utilisant Visual Studio interface utilisateur de contrôle source (UI). Un contrôle source VSPackage, d’autre part, fournit [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] un nouveau chemin d’intégration profonde adapté à l’intégration de contrôle des sources qui exige un haut niveau de sophistication et d’autonomie dans son modèle de contrôle source.

 ![Vue d'ensemble du contrôle de code source](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Plug-in de contrôle des sources
 Toutes les versions de Visual Studio prennent en charge la version de spécifications 1.2 de Contrôle Source Plug-in comme voie d’intégration. Un implémenteur de contrôle source de plug-in écrit un DLL qui implémente les fonctions d’API de contrôle source pour l’intégration et l’enregistrement de contrôle des sources comme décrit dans [La création d’un plug-in de contrôle source](../../extensibility/internals/creating-a-source-control-plug-in.md). Dans cette approche, l’Environnement intégré de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] développement (IDE) utilise l’interface utilisateur pour les boîtes de dialogue, telles que l’enregistrement, la caisse, les pages de propriété d’outils/options, les barres d’outils et les glyphes de contrôle source. Une stricte adhésion à l’API plug-in Source Control assure une intégration facile dans Visual Studio et une expérience sans problème pour l’utilisateur. Cela signifie que le plug-in de contrôle source doit implémenter la plupart des fonctions et des rappels détaillés dans l’API.

 Pour implémenter un plug-in de contrôle source à l’aide de l’API rechargeable source de contrôle, suivez ces étapes :

1. Créez un DLL qui implémente les fonctions spécifiées dans [les plug-ins source Control](../../extensibility/source-control-plug-ins.md).

2. Enregistrez le DLL en faisant les entrées de registre appropriées (décrites dans [Comment : Installer un plug-in de contrôle source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).

3. Créez une interface utilisateur et un affichage d’aide lorsqu’il est incité par le paquet d’adaptateur de contrôle des sources (le composant Visual Studio qui gère la fonctionnalité de contrôle des sources via les plug-ins de contrôle source)

   En réponse à une commande de contrôle source, le Visual Studio IDE présente une interface utilisateur standard pour les opérations de base, puis transmet les informations au plug-in de contrôle source via les fonctions définies dans l’API de contrôle source. Pour les options avancées, le plug-in de contrôle source peut être appelé à présenter sa propre interface utilisateur, par exemple, la navigation pour un projet contrôlé par la source. Cela signifie que l’utilisateur peut être présenté avec deux styles d’interface utilisateur peut-être différents lorsqu’il s’agit de contrôle source: l’interface utilisateur que Visual Studio présente et l’interface utilisateur que le plug-in de contrôle source présente. Ceci est plus notable avec les opérations avancées de contrôle de source.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Inconvénients à la mise en œuvre d’un plug-in de contrôle des sources

- Pour les fonctionnalités avancées, l’utilisateur peut voir deux styles différents d’interfaces, conduisant à une confusion possible.

- Le plug-in de contrôle source est limité au modèle de contrôle source implicite par l’API de contrôle source.

- L’API de contrôle source peut être trop restrictive pour certains scénarios de contrôle des sources.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Avantages à la mise en œuvre d’un plug-in de contrôle des sources

- Visual Studio fournit toute l’interface utilisateur pour toutes les opérations de contrôle source de base afin que le plug-in de contrôle source n’ait pas à implémenter l’interface utilisateur potentiellement complexe.

- En raison de l’API stricte, le plug-in de contrôle source peut facilement interagir avec les programmes externes de contrôle des sources pour fournir des fonctionnalités plus étendues; Visual Studio ne se soucie pas trop de la façon dont la fonctionnalité de contrôle source est accomplie, seulement qu’il est accompli selon l’API de contrôle source plug-in.

- Il est plus facile d’implémenter un plug-in de contrôle source qu’un VSPackage de contrôle source.

## <a name="source-control-vspackage"></a>Contrôle des sources VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]permet une intégration approfondie dans Visual Studio avec un contrôle total de la fonctionnalité de contrôle des sources et le remplacement complet de l’interface utilisateur de contrôle source fournie par Visual Studio. Un contrôle source VSPackage est enregistré auprès de Visual Studio et fournit des fonctionnalités de contrôle source. Bien que plusieurs VSPackages de contrôle source puissent être enregistrés auprès de Visual Studio, un seul d’entre eux peut être actif à tout moment. Un contrôle source VSPackage a le plein contrôle sur la fonctionnalité de contrôle source et l’apparence dans Visual Studio alors qu’il est actif. Tous les autres VSPackages de contrôle source qui peuvent être enregistrés dans le système sont inactifs et n’afficheront aucune interface utilisateur du tout.

 La mise en œuvre d’un contrôle source VSPackage nécessite une stratégie « tout ou rien ». Le créateur d’un contrôle source VSPackage doit investir une quantité importante d’efforts dans la mise en œuvre d’un certain nombre d’interfaces de contrôle source et de nouveaux éléments d’interface utilisateur (boîtes de dialogue, menus et barres d’outils) pour couvrir l’ensemble des fonctionnalités de contrôle des sources. Voir [Créer un contrôle source VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md) pour plus de détails.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Inconvénients à la mise en œuvre d’un VSPackage de contrôle des sources

- Le VSPackage doit implémenter un certain nombre d’interfaces complexes pour s’intégrer avec succès avec Visual Studio.

- Le VSPackage doit fournir toute l’interface utilisateur requise pour le contrôle des sources; Visual Studio ne fournira aucune aide dans ce domaine.

- Un contrôle source VSPackage est intimement lié à Visual Studio et ne peut pas fonctionner avec des programmes autonomes, de sorte que la fonctionnalité ne peut pas être aussi facilement partagée avec une version externe du programme de contrôle source.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Avantages à la mise en œuvre d’un VSPackage de contrôle des sources

- Parce que le VSPackage a le plein contrôle sur l’interface utilisateur de contrôle source et la fonctionnalité, l’utilisateur est présenté avec une interface transparente pour le contrôle de la source.

- Le VSPackage ne se limite pas à un modèle de contrôle source particulier.

## <a name="see-also"></a>Voir aussi
- [Contrôle des sources](../../extensibility/internals/source-control.md)
- [Création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Création d’un VSPackage de contrôle de code source](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Nouveautés du contrôle de code source](../../extensibility/internals/what-s-new-in-source-control.md)

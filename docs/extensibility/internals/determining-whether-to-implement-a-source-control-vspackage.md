---
title: Déterminer s’il faut mettre en œuvre un VSPackage de contrôle des sources (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8707f3c1ced1cc2df9d3ae77280fc8779874a837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708724"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Déterminer s’il faut mettre en œuvre un contrôle source VSPackage
Cette section élabore les choix des plug-ins de contrôle des sources et des VSPackages de contrôle des sources pour l’extension des solutions de contrôle des sources et donne de larges lignes directrices sur le choix d’une voie d’intégration appropriée.

## <a name="small-source-control-solution-with-limited-resources"></a>Solution de contrôle des petites sources avec des ressources limitées
 Si vous avez des ressources limitées et ne pouvez pas être accablé par les frais généraux de la rédaction d’un paquet de contrôle source, vous pouvez créer Source Control Plug-in API-based plug-in plug-ins. Ce qui vous permet de travailler côte à côte avec des paquets de contrôle source, et vous pouvez passer entre les plug-ins de contrôle source et les paquets à la demande. Pour plus d’informations, voir [Inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Grande solution de contrôle de source avec un ensemble de fonctionnalités riche
 Si vous souhaitez implémenter une solution de contrôle source qui fournit un modèle de contrôle source riche qui n’est pas correctement capturé en utilisant l’API de contrôle source plug-in, vous pouvez considérer un paquet de contrôle source comme la voie d’intégration. Cela s’applique surtout si vous préférez remplacer le paquet d’adaptateur de contrôle des sources (qui communique avec des plug-ins de contrôle source et fournit une interface utilisateur de contrôle source de base) avec votre propre afin que vous puissiez gérer les événements de contrôle source d’une manière personnalisée. Si vous avez déjà une interface utilisateur de contrôle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]source satisfaisante et que vous souhaitez préserver cette expérience dans , l’option de contrôle source paquet vous permet de le faire. Le paquet de contrôle source n’est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pas générique et est conçu uniquement pour une utilisation avec IDE.

 Si vous souhaitez implémenter une solution de contrôle source qui offre une flexibilité et un contrôle plus riche sur la logique de contrôle source et l’interface utilisateur, vous pouvez préférer l’itinéraire d’intégration du paquet de contrôle source. Vous pouvez :

1. Enregistrez votre propre contrôle source VSPackage (voir [Inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Remplacez l’interface utilisateur de contrôle source par défaut par votre interface utilisateur personnalisée (voir [interface utilisateur personnalisée).](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

3. Spécifier les glyphes à utiliser et gérer les événements de glyphe solution Explorer (voir [contrôle Glyph](../../extensibility/internals/glyph-control-source-control-vspackage.md)).

4. Handle Query Edit and Query Save events (voir [Requête Edit Requête Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).

## <a name="see-also"></a>Voir aussi
- [Créer un plug-in de contrôle source](../../extensibility/internals/creating-a-source-control-plug-in.md)

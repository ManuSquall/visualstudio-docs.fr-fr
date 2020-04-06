---
title: Démarrer avec les plug-ins de contrôle des sources Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efc21e07830614d9d3041b2d2d231fd82c652114
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708347"
---
# <a name="get-started-with-source-control-plug-ins"></a>Démarrer avec des plug-ins de contrôle de source
Pour créer un plug-in de contrôle source, vous devez créer un DLL qui implémente les fonctions [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] définies dans l’API de contrôle source, puis pour enregistrer le DLL avec pour le rendre disponible pour une utilisation dans le contrôle de version de code source.

 Trois versions de l’API de contrôle source (versions 1.1, 1.2 et 1.3) sont disponibles pour les plug-ins de contrôle source. L’API de contrôle source documenté ici est la version 1.3. Il a été conçu pour être entièrement compatible avec les plug-ins de contrôle source soutenant les versions 1.1 et 1.2. Le quoi est nouveau dans la version [plug-in de contrôle source API Version 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) détaille les nouvelles fonctionnalités prises en charge dans la dernière version de l’API de contrôle source plug-in.

## <a name="in-this-section"></a>Contenu de cette section
- [Comment : Installer un plug-in de contrôle source](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 Décrit comment faire les entrées de registre qui sont nécessaires pour brancher un contrôle source DLL.

- [Nouveauté dans la version API 1.3 du contrôle source](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 Fournit un bref aperçu des modifications apportées à l’API rechargeable de contrôle des sources dans la version 1.3.

- [Nouveauté dans la version API 1.2 du contrôle source](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 Fournit un bref aperçu des modifications apportées à l’API rechargeable de contrôle source dans la version 1.2.

## <a name="related-sections"></a>Sections connexes
- [Plug-ins de contrôle des sources](../../extensibility/source-control-plug-ins.md)

 Fournit une liste complète de tous les éléments de l’API rechargeable de contrôle source.

- [Créer un plug-in de contrôle source](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Définit le SDK de contrôle source et décrit les ressources incluses.

---
title: Gestion des EMBALLAGEs VS (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60745d07679ae53b85d169473ed37ab314b67624
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702653"
---
# <a name="manage-vspackages"></a>Gérer VSPackages
Dans la plupart des cas, vous n’avez pas besoin de vous soucier de la gestion des VSPackages, puisque les modèles de projet et d’article s’inscrivent et chargent le paquet automatiquement. Cependant, dans certaines circonstances, vous devrez peut-être en apprendre un peu plus afin de gérer votre colis.

## <a name="use-the-experimental-instance"></a>Utiliser l’instance expérimentale
 Pour en savoir plus sur l’instance expérimentale, voir [L’instance expérimentale](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Inscrivez-vous et enregistrez VSPackages
 Pour savoir comment s’inscrire et non enregistrer VSPackages et d’autres types d’extension, voir [Registre et non enregistré VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Chargez un VSPackage
 VSPackages peut être réglé pour recharger automatiquement quand un GUID CMDUICONTEXT particulier est activé. Pour plus d’informations, voir [Load VSPackages](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Utilisez AsyncPackage pour charger VSPackages en arrière-plan
 La `AsyncPackage` classe permet le chargement de l’emballage sur un fil de fond pour une meilleure réactivité de l’interface utilisateur dans Visual Studio. Pour plus d’informations, voir [Comment: Utilisez AsyncPackage pour charger VSPackages en arrière-plan](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Contexte d’interface utilisateur fondé sur des règles pour les extensions
 Les contextes d’interface utilisateur basés sur des règles permettent aux auteurs d’extension de définir les conditions précises dans lesquelles un contexte d’interface utilisateur est activé et les VSPackages associés chargés. Pour plus d’informations, voir Comment : Utilisez le [contexte d’interface utilisateur basé sur les règles pour les extensions Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Diagnostiquer les performances de l’extension
Les extensions peuvent avoir un impact sur les performances de démarrage et de charge de solution. Découvrez comment l’impact de l’extension visual Studio est calculé et comment il peut être analysé localement pour tester si une extension peut être affichée comme une extension d’impact sur les performances. Pour plus d’informations, voir [Comment : Diagnostiquer les performances d’extension.](how-to-diagnose-extension-performance.md)

## <a name="troubleshoot-vspackages"></a>Dépannage VSPackages
 Découvrez les techniques de dépannage des VSPackages qui ne se chargent pas ou qui éprouvent des erreurs : [Dépannage VSPackages](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Voir aussi
- [VSPackages](../extensibility/internals/vspackages.md)

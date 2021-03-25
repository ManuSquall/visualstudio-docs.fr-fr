---
title: Gestion des VSPackages | Microsoft Docs
description: Apprenez-en davantage sur la gestion des VSPackages, afin de savoir quand vous pouvez simplement utiliser la gestion VSPackage par défaut fournie par Visual Studio, et comment et quand le personnaliser.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a62581e036b70a10db533dc46d0787cd558afe29
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090627"
---
# <a name="manage-vspackages"></a>Gérer VSPackages
Dans la plupart des cas, vous n’avez pas à vous soucier de la gestion des VSPackages, puisque les modèles de projet et d’élément s’inscrivent et chargent automatiquement le package. Toutefois, dans certains cas, vous devrez peut-être en apprendre un peu plus pour gérer votre package.

## <a name="use-the-experimental-instance"></a>Utiliser l’instance expérimentale
 Pour en savoir plus sur l’instance expérimentale, consultez [l’instance expérimentale](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Inscrire et désinscrire des VSPackages
 Pour savoir comment inscrire et désinscrire des VSPackages et d’autres types d’extension, consultez [inscrire et désinscrire des VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Charger un VSPackage
 Les VSPackages peuvent être définis sur autoload lorsqu’un GUID CMDUICONTEXT particulier est activé. Pour plus d’informations, consultez [charger des VSPackages](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Utiliser AsyncPackage pour charger les VSPackages en arrière-plan
 La `AsyncPackage` classe active le chargement des packages sur un thread d’arrière-plan pour une meilleure réactivité de l’interface utilisateur dans Visual Studio. Pour plus d’informations, consultez [Comment : utiliser AsyncPackage pour charger des VSPackages en arrière-plan](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Contexte de l’interface utilisateur basé sur des règles pour les extensions
 Les contextes d’interface utilisateur basés sur des règles permettent aux auteurs d’extensions de définir les conditions précises sous lesquelles un contexte d’interface utilisateur est activé et les VSPackages associés chargés. Pour plus d’informations, consultez [Comment : utiliser le contexte de l’interface utilisateur basé sur des règles pour les extensions Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Diagnostiquer les performances de l’extension
Les extensions peuvent avoir un impact sur les performances de démarrage et de chargement de solution. Découvrez comment l’impact des extensions Visual Studio est calculé et comment il peut être analysé localement pour tester si une extension peut être affichée en tant qu’extension d’impact sur les performances. Pour plus d’informations, consultez [Comment : diagnostiquer les performances des extensions](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Résoudre les problèmes liés aux VSPackages
 Découvrez les techniques de dépannage des VSPackages qui ne se chargent pas ou qui rencontrent des erreurs : [résoudre les problèmes liés aux VSPackages](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Voir aussi
- [VSPackages](../extensibility/internals/vspackages.md)

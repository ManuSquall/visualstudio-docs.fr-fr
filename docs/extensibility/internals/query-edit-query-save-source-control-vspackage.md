---
title: Requête modifier la requête enregistrer (VSPackage de contrôle de code source) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be12297bdaeb112d7421b02da1153ed62d6d14f8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724771"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Modifier la requête Enregistrer la requête (VSPackage de contrôle de code source)
les éditeurs de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peuvent diffuser des événements de requête de modification de requête (provenant QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stub de contrôle de code source implémente le service provenant QEQS, afin qu’il soit le destinataire des événements provenant QEQS. Ces événements sont ensuite délégués au VSPackage de contrôle de code source actuellement actif. Le VSPackage de contrôle de code source actif implémente le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> et ses méthodes. Les méthodes de l’interface `IVsQueryEditQuerySave2` sont généralement appelées immédiatement avant qu’un document soit modifié pour la première fois et juste avant l’enregistrement d’un document.

## <a name="queryeditquerysave-events"></a>Événements QueryEditQuerySave
 Le VSPackage de contrôle de code source doit gérer les événements provenant QEQS en implémentant l’interface `IVsQueryEditQuerySave2` et les méthodes nécessaires. Vous trouverez ci-dessous une brève description des deux méthodes que le VSPackage doit implémenter au minimum. L’implémentation réelle doit être conforme à la logique du modèle de contrôle de code source.

### <a name="queryeditfiles-method"></a>Méthode QueryEditFiles
 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> est appelée lorsqu’un projet ou un éditeur souhaite modifier un fichier. Dans l’idéal, cette méthode est appelée *avant* la modification du fichier et lors de l’enregistrement d’un fichier. Lorsqu’elle est appelée, la méthode `IVsQueryEditQuerySave2::QueryEditFiles` vérifie si les fichiers spécifiés sont sous contrôle de code source, s’ils doivent être extraits et s’ils peuvent être rechargés. Si des circonstances empêchent la modification des fichiers, la méthode `IVsQueryEditQuerySave2::QueryEditFiles` indique au programme appelant d’annuler la modification. L’appelant peut également spécifier un mode d’appel. En mode « sans assistance », cette méthode n’effectue d’action que si elle n’entraîne pas l’affichage d’une interface utilisateur. Si l’interface utilisateur est inévitable, un indicateur doit être retourné pour indiquer le problème.

 La méthode se comporte de manière transactionnelle ; autrement dit, si la modification est annulée sur un seul fichier, la modification est annulée pour tous les fichiers. À l’inverse, si la modification est autorisée, elle est autorisée pour tous les fichiers. Si cette méthode autorise la modification une seule fois pour un ensemble de fichiers donné, elle doit toujours autoriser la modification sur les appels suivants pour le même ensemble de fichiers. La boucle allow-Edit continue jusqu’à ce que les fichiers soient fermés, enregistrés et rechargés ; jusqu’à ce que leurs attributs (propriétés) changent ; ou jusqu’à ce que le package de contrôle de code source soit modifié. Les cas à prendre en compte lors de l’implémentation de la méthode `IVsQueryEditQuerySave2::QueryEditFiles` incluent plusieurs fichiers, des fichiers spéciaux, l’annulation de l’utilisateur et les modifications en mémoire.

### <a name="querysavefiles-method"></a>Méthode QuerySaveFiles
 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> est appelée quand un projet ou un éditeur doit enregistrer un ensemble de fichiers. Lorsqu’elle est appelée, la méthode `IVsQueryEditQuerySave2::QuerySaveFiles` vérifie si les fichiers spécifiés sont en lecture seule et s’ils sont sous contrôle de code source. Si les fichiers doivent être extraits, l’appel est délégué au package de contrôle de code source. Si des circonstances empêchent l’enregistrement des fichiers, la méthode `IVsQueryEditQuerySave2::QuerySaveFiles` doit indiquer à l’éditeur d’annuler l’enregistrement. Comme avec la méthode `IVsQueryEditQuerySave2::QueryEditFiles`, l’appelant peut spécifier un mode d’appel. En mode « sans assistance », cette méthode n’effectue d’action que si elle n’entraîne pas l’affichage d’une interface utilisateur. Si l’interface utilisateur est inévitable, un indicateur doit être retourné pour indiquer le problème.

 Cette méthode doit se comporter de manière transactionnelle ; autrement dit, si l’enregistrement est annulé sur un seul fichier, l’enregistrement est annulé pour tous les fichiers. À l’inverse, si l’enregistrement est autorisé, il doit être autorisé pour tous les fichiers. Comme avec la méthode `IVsQueryEditQuerySave2::QueryEditFiles`, les cas à prendre en compte lors de l’implémentation de la méthode `IVsQueryEditQuerySave2::QuerySaveFiles` incluent plusieurs fichiers, des fichiers spéciaux, des annulations de l’utilisateur et des modifications en mémoire.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
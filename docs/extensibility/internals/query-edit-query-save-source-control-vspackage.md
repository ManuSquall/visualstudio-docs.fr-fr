---
title: Requête modifier la requête enregistrer (VSPackage de contrôle de code source) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c09ac0cb4f51b8f2484b95d403ff6d0445631479
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705971"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Modifier la requête Enregistrer la requête (VSPackage de contrôle de code source)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les éditeurs peuvent diffuser des événements de requête de modification de requête (provenant QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Le stub de contrôle de code source implémente le service provenant QEQS, afin qu’il soit le destinataire des événements provenant QEQS. Ces événements sont ensuite délégués au VSPackage de contrôle de code source actuellement actif. Le VSPackage de contrôle de code source actif implémente les <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> méthodes et. Les méthodes de l' `IVsQueryEditQuerySave2` interface sont généralement appelées juste avant qu’un document soit modifié pour la première fois et juste avant l’enregistrement d’un document.

## <a name="queryeditquerysave-events"></a>Événements QueryEditQuerySave
 Le VSPackage de contrôle de code source doit gérer les événements provenant QEQS en implémentant l' `IVsQueryEditQuerySave2` interface et les méthodes nécessaires. Vous trouverez ci-dessous une brève description des deux méthodes que le VSPackage doit implémenter au minimum. L’implémentation réelle doit être conforme à la logique du modèle de contrôle de code source.

### <a name="queryeditfiles-method"></a>Méthode QueryEditFiles
 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> méthode est appelée quand un projet ou un éditeur souhaite modifier un fichier. Dans l’idéal, cette méthode est appelée *avant* la modification du fichier et lors de l’enregistrement d’un fichier. Lorsqu’elle est appelée, la `IVsQueryEditQuerySave2::QueryEditFiles` méthode vérifie si les fichiers spécifiés sont sous contrôle de code source, s’ils doivent être extraits et s’ils peuvent être rechargés. Si des circonstances empêchent la modification des fichiers, la `IVsQueryEditQuerySave2::QueryEditFiles` méthode indique au programme appelant d’annuler la modification. L’appelant peut également spécifier un mode d’appel. En mode « sans assistance », cette méthode n’effectue d’action que si elle n’entraîne pas l’affichage d’une interface utilisateur. Si l’interface utilisateur est inévitable, un indicateur doit être retourné pour indiquer le problème.

 La méthode se comporte de manière transactionnelle ; autrement dit, si la modification est annulée sur un seul fichier, la modification est annulée pour tous les fichiers. À l’inverse, si la modification est autorisée, elle est autorisée pour tous les fichiers. Si cette méthode autorise la modification une seule fois pour un ensemble de fichiers donné, elle doit toujours autoriser la modification sur les appels suivants pour le même ensemble de fichiers. La boucle allow-Edit continue jusqu’à ce que les fichiers soient fermés, enregistrés et rechargés ; jusqu’à ce que leurs attributs (propriétés) changent ; ou jusqu’à ce que le package de contrôle de code source soit modifié. Les cas à prendre en compte lors de l’implémentation de la `IVsQueryEditQuerySave2::QueryEditFiles` méthode incluent plusieurs fichiers, des fichiers spéciaux, l’annulation de l’utilisateur et les modifications en mémoire.

### <a name="querysavefiles-method"></a>Méthode QuerySaveFiles
 La <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> méthode est appelée quand un projet ou un éditeur doit enregistrer un ensemble de fichiers. Lorsqu’elle est appelée, la `IVsQueryEditQuerySave2::QuerySaveFiles` méthode vérifie si les fichiers spécifiés sont en lecture seule et s’ils sont sous contrôle de code source. Si les fichiers doivent être extraits, l’appel est délégué au package de contrôle de code source. Si des circonstances empêchent l’enregistrement des fichiers, la `IVsQueryEditQuerySave2::QuerySaveFiles` méthode doit indiquer à l’éditeur d’annuler l’enregistrement. Comme avec la `IVsQueryEditQuerySave2::QueryEditFiles` méthode, l’appelant peut spécifier un mode d’invocation. En mode « sans assistance », cette méthode n’effectue d’action que si elle n’entraîne pas l’affichage d’une interface utilisateur. Si l’interface utilisateur est inévitable, un indicateur doit être retourné pour indiquer le problème.

 Cette méthode doit se comporter de manière transactionnelle ; autrement dit, si l’enregistrement est annulé sur un seul fichier, l’enregistrement est annulé pour tous les fichiers. À l’inverse, si l’enregistrement est autorisé, il doit être autorisé pour tous les fichiers. Comme avec la `IVsQueryEditQuerySave2::QueryEditFiles` méthode, les cas à prendre en compte lors de l’implémentation de la `IVsQueryEditQuerySave2::QuerySaveFiles` méthode incluent plusieurs fichiers, des fichiers spéciaux, l’annulation de l’utilisateur et les modifications en mémoire.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>

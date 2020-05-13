---
title: Requête Edit Requête Save (Source Control VSPackage) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705971"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Modifier la requête Enregistrer la requête (VSPackage de contrôle de code source)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]les éditeurs peuvent diffuser des événements Requête Edit Requête Save (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Source Control Stub met en œuvre le service QEQS, de sorte qu’il est le bénéficiaire d’événements QEQS. Ces événements sont ensuite délégués au contrôle source actuellement actif VSPackage. Le contrôle source actif VSPackage met en œuvre les <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> méthodes et ses méthodes. Les méthodes `IVsQueryEditQuerySave2` de l’interface sont généralement appelées immédiatement avant qu’un document soit modifié pour la première fois et immédiatement avant qu’un document soit enregistré.

## <a name="queryeditquerysave-events"></a>Événements QueryEditQuerySave
 Le contrôle source VSPackage doit gérer les événements `IVsQueryEditQuerySave2` QEQS en mettant en œuvre l’interface et les méthodes nécessaires. Voici une brève description des deux méthodes que le VSPackage doit mettre en œuvre au minimum. La mise en œuvre réelle doit être conforme à la logique du modèle de contrôle source.

### <a name="queryeditfiles-method"></a>Méthode RequêteEditFiles
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> est appelé quand un projet ou un éditeur veut modifier un fichier. Idéalement, cette méthode est appelée *avant* que le fichier soit modifié et lorsqu’un fichier est enregistré. Lorsqu’elle est `IVsQueryEditQuerySave2::QueryEditFiles` invoquée, la méthode vérifie si les fichiers donnés sont sous contrôle source, s’ils doivent être vérifiés et s’ils peuvent être rechargés. Si les circonstances empêchent les fichiers `IVsQueryEditQuerySave2::QueryEditFiles` d’être modifiables, la méthode indique au programme d’appel d’annuler la modification. Il est également possible pour l’appelant de spécifier un mode d’invocation. Dans le mode "silencieux", cette méthode ne prend des mesures que si elle ne provoque pas d’interface utilisateur. Si l’interface utilisateur est inévitable, un drapeau doit être retourné pour indiquer le problème.

 La méthode se comporte de manière transactionnelle; c’est-à-dire que si la modification est annulée sur un seul fichier, la modification est annulée pour tous les fichiers. Inversement, si la modification est autorisée, elle est autorisée pour tous les fichiers. Si cette méthode permet l’édition une fois pour un ensemble donné de fichiers, elle doit toujours permettre l’édition sur les appels ultérieurs pour le même ensemble de fichiers. La boucle d’autorisation-modification se poursuit jusqu’à ce que les fichiers soient fermés, enregistrés et rechargés; jusqu’à ce que leurs attributs (propriétés) changent; ou jusqu’à ce que le paquet de contrôle source soit modifié. Les cas à prendre `IVsQueryEditQuerySave2::QueryEditFiles` en considération dans la mise en œuvre de la méthode comprennent plusieurs fichiers, fichiers spéciaux, annulation de l’utilisateur et modifications en mémoire.

### <a name="querysavefiles-method"></a>Méthode RequêteSaveFiles
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> s’appelle lorsque tout projet ou éditeur doit enregistrer un ensemble de fichiers. Lorsqu’elle est `IVsQueryEditQuerySave2::QuerySaveFiles` invoquée, la méthode vérifie si les fichiers donnés sont lus uniquement et s’ils sont sous contrôle source. Si les fichiers doivent être vérifiés, l’appel est délégué au paquet de contrôle source. Si les circonstances empêchent l’enregistrement des fichiers, la `IVsQueryEditQuerySave2::QuerySaveFiles` méthode doit indiquer à l’éditeur d’annuler l’enregistrement. Comme avec `IVsQueryEditQuerySave2::QueryEditFiles` la méthode, il est possible pour l’appelant de spécifier un mode d’invocation. Dans le mode "silencieux", cette méthode ne prend des mesures que si elle ne provoque pas d’interface utilisateur. Si l’interface utilisateur est inévitable, un drapeau doit être retourné pour indiquer le problème.

 Cette méthode doit se comporter de manière transactionnelle; c’est-à-dire que si l’enregistrement est annulé sur un seul fichier, l’enregistrement est annulé pour tous les fichiers. Inversement, si l’enregistrement est autorisé, il doit être autorisé pour tous les fichiers. Comme avec `IVsQueryEditQuerySave2::QueryEditFiles` la méthode, les cas `IVsQueryEditQuerySave2::QuerySaveFiles` à considérer dans la mise en œuvre de la méthode comprennent plusieurs fichiers, fichiers spéciaux, annuler de l’utilisateur, et les modifications en mémoire.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>

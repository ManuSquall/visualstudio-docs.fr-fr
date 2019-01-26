---
title: Modifier la requête d’enregistrement (VSPackage de contrôle de code Source) de requête | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d001e324352c566d71e66ae26d769cc8f3c2f644
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011515"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Modifier la requête Enregistrer la requête (VSPackage de contrôle de code source)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les éditeurs peuvent diffuse les événements de requête modifier requête enregistrer (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Stub de contrôle source implémente le service QEQS, afin qu’il soit le destinataire d’événements QEQS. Ces événements sont alors délégués pour le VSPackage de contrôle source actuellement active. Le contrôle de source active VSPackage implémente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> et ses méthodes. Les méthodes de la `IVsQueryEditQuerySave2` interface sont généralement appelées immédiatement avant la modification d’un document pour la première fois et immédiatement avant l’enregistrée d’un document.  
  
## <a name="queryeditquerysave-events"></a>Événements de QueryEditQuerySave  
 Le contrôle de code source VSPackage doit gérer les événements QEQS en implémentant le `IVsQueryEditQuerySave2` interface et les méthodes nécessaires. Voici une brève description des deux méthodes que le VSPackage doit implémenter au minimum. L’implémentation réelle doit être conformément à la logique du modèle de contrôle source.  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles (méthode)  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> est appelée lorsqu’un projet ou un éditeur souhaite modifier un fichier. Dans l’idéal, cette méthode est appelée *avant* le fichier est modifié et quand un fichier est enregistré. Lorsqu’elle est appelée, le `IVsQueryEditQuerySave2::QueryEditFiles` méthode vérifie si les fichiers donnés sont sous contrôle de code source, s’ils doivent être extraits, et si elles peuvent être rechargées. Si les circonstances empêchent les fichiers modifiables, le `IVsQueryEditQuerySave2::QueryEditFiles` méthode indique au programme appelant pour annuler la modification. Il est également possible que l’appelant de spécifier un mode d’appel. Dans le mode « silencieux », cette méthode intervient uniquement si elle n’entraîne pas d’interface utilisateur apparaisse. Si l’interface utilisateur est inévitable, un indicateur doit être retourné pour indiquer le problème.  
  
 La méthode se comporte de façon transactionnelle ; Autrement dit, si la modification est annulée sur un seul fichier, la modification est annulée pour tous les fichiers. À l’inverse, si la modification est autorisée, il est autorisé pour tous les fichiers. Si cette méthode permet de modifier une seule fois pour un ensemble donné de fichiers, il doit toujours autoriser la modification sur les appels suivants pour le même ensemble de fichiers. La boucle d’autoriser de modification continue jusqu'à ce que les fichiers sont fermés, enregistrés et rechargés ; jusqu'à ce que la modification de leurs attributs (propriétés) ; ou jusqu'à ce que le package de contrôle de code source est modifié. Cas à prendre en compte dans l’implémentation de la `IVsQueryEditQuerySave2::QueryEditFiles` méthode inclure plusieurs fichiers, des fichiers spéciaux, annulez d’utilisateur et des modifications en mémoire.  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles (méthode)  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> est appelée lorsqu’un projet ou un éditeur doit enregistrer un ensemble de fichiers. Lorsqu’elle est appelée, le `IVsQueryEditQuerySave2::QuerySaveFiles` méthode vérifie si les fichiers donnés sont en lecture seule et s’ils sont sous contrôle de code source. Si les fichiers doivent être extraits, l’appel est déléguée pour le package de contrôle de code source. Si des circonstances empêchent les fichiers ne sont pas enregistrées, la `IVsQueryEditQuerySave2::QuerySaveFiles` méthode doit indiquer à l’éditeur pour annuler l’enregistrement. Comme avec la `IVsQueryEditQuerySave2::QueryEditFiles` (méthode), il est possible pour l’appelant de spécifier un mode d’appel. Dans le mode « silencieux », cette méthode intervient uniquement si elle n’entraîne pas d’interface utilisateur apparaisse. Si l’interface utilisateur est inévitable, un indicateur doit être retourné pour indiquer le problème.  
  
 Cette méthode doit se comporter de façon transactionnelle ; Autrement dit, si l’enregistrement est annulé sur un seul fichier, l’enregistrement est annulé pour tous les fichiers. À l’inverse, si l’enregistrement est autorisée, il doit être autorisé pour tous les fichiers. Comme avec la `IVsQueryEditQuerySave2::QueryEditFiles` (méthode), le cas à prendre en compte dans l’implémentation de la `IVsQueryEditQuerySave2::QuerySaveFiles` méthode inclure plusieurs fichiers, des fichiers spéciaux, annulez d’utilisateur et des modifications en mémoire.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
---
title: "Modifier la requ&#234;te requ&#234;te enregistrer (VSPackage du contr&#244;le de code Source) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Événements QEQS"
  - "Modifier les requêtes enregistrer les événements de requête"
  - "packages de contrôle de code source, Query modifier requête enregistre les événements"
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Modifier la requ&#234;te requ&#234;te enregistrer (VSPackage du contr&#244;le de code Source)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

les éditeurs de[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peuvent diffuser des événements de sauvegarde de modifier la \(QEQS\) requête de requête.  le stub de contrôle de code source de[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implémente le service de QEQS, afin d'être destinataire d'événements de QEQS.  Ces événements sont ensuite délégués à atteindre au contrôle de code source actif VSPackage.  le contrôle de code source actif VSPackage applique <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> et ses méthodes.  Les méthodes d'interface d' `IVsQueryEditQuerySave2` sont généralement appelées immédiatement avant qu'un document a été modifié pour la première fois et juste avant qu'un document est enregistré.  
  
## événements de QueryEditQuerySave  
 le contrôle de code source VSPackage doit gérer les événements de QEQS en implémentant l'interface d' `IVsQueryEditQuerySave2` et les méthodes nécessaires.  Vous trouverez ci\-dessous une description courte des deux méthodes que le VSPackage doit implémenter minimale.  l'implémentation réelle doit être conforme à la logique du modèle de contrôle de code source.  
  
### méthode de QueryEditFiles  
 L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> est appelé à tout projet ou éditeur souhaite modifier un fichier.  Idéalement, cette méthode est appelée *avant* que le fichier est modifié et lorsqu'un fichier est enregistré.  Lorsqu'elle est appelée, la méthode d' `IVsQueryEditQuerySave2::QueryEditFiles` vérifie si les fichiers sont fournis sous contrôle de code source, s'ils doivent être vérifiés, et si elles peuvent être rechargés.  Si les circonstances empêchent les fichiers d'être modifiables, la méthode d' `IVsQueryEditQuerySave2::QueryEditFiles` indique au programme appelant annuler la modification.  il est également possible que l'appelant spécifie un mode d'appel.  En mode silencieux «  », cette méthode fonctionne uniquement si elle ne fait apparaître aucune interface utilisateur.  Si l'interface utilisateur est inévitable, une balise doit être retourné pour indiquer le problème.  
  
 La méthode se comporte de manière transactionnels ; autrement dit, si la modification est annulée sur un fichier unique, la modification est annulée pour tous les fichiers.  Inversement, s'il autorise la modification, il lui permet de tous les fichiers.  Si cette méthode permet la modification une fois pour un ensemble donné de fichiers, elle doit toujours autoriser la modification lors de les appels suivants pour le même jeu de fichiers.  la boucle d'autoriser\-modification continue jusqu'à ce que les fichiers soient fermés, enregistrés, et rechargés ; jusqu'à leur modification d'attributs \(propriétés\) ; ou jusqu'à ce que le contrôle de code source le package est modifié.  Les cas à prendre en compte en implémentant la méthode d' `IVsQueryEditQuerySave2::QueryEditFiles` incluent plusieurs fichiers, les fichiers spéciaux, l'annulation de l'utilisateur, et les modifications en mémoire.  
  
### méthode de QuerySaveFiles  
 L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> est appelé à tout projet ou éditeur doit enregistrer des fichiers.  Lorsqu'elle est appelée, la méthode d' `IVsQueryEditQuerySave2::QuerySaveFiles` vérifie si les fichiers fournis sont en lecture seule et s'ils soient sous contrôle de code source.  Si les fichiers doivent être vérifiés, l'appel est délégué au package de contrôle de code source.  Si les circonstances empêchent les fichiers d'être enregistré, la méthode d' `IVsQueryEditQuerySave2::QuerySaveFiles` doit pointer vers l'éditeur annuler l'enregistrement.  comme avec la méthode d' `IVsQueryEditQuerySave2::QueryEditFiles` , il est possible que l'appelant spécifie un mode d'appel.  En mode silencieux «  », cette méthode fonctionne uniquement si elle ne fait apparaître aucune interface utilisateur.  Si l'interface utilisateur est inévitable, une balise doit être retourné pour indiquer le problème.  
  
 Cette méthode doit se comporter de façon transactionnels ; autrement dit, si la sauvegarde est annulée sur un fichier unique, d'enregistrement est annulée pour tous les fichiers.  Inversement, si est autorisée à enregistrer, il doit être autorisé pour tous les fichiers.  Comme avec la méthode d' `IVsQueryEditQuerySave2::QueryEditFiles` , les cas à prendre en compte en implémentant la méthode d' `IVsQueryEditQuerySave2::QuerySaveFiles` incluent plusieurs fichiers, les fichiers spéciaux, l'annulation de l'utilisateur, et les modifications en mémoire.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
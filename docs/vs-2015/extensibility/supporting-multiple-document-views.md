---
title: Prise en charge de plusieurs vues de documents | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9377fc12db8cedba65a418fd32b82a1421bd9b43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160528"
---
# <a name="supporting-multiple-document-views"></a>Prise en charge de vues de document multiples
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez fournir plusieurs vues d’un document en créant des données de document et des objets de vue de document distincts pour votre éditeur. Voici quelques cas dans lesquels une vue de document supplémentaire serait utile :  
  
- Prise en charge des nouvelles fenêtres : vous souhaitez que votre éditeur fournisse deux vues ou plus du même type, afin qu’un utilisateur qui a déjà une fenêtre ouverte dans l’éditeur puisse ouvrir une nouvelle fenêtre en sélectionnant la commande **nouvelle fenêtre** dans le menu **fenêtre** .  
  
- Prise en charge des modes formulaire et code : vous souhaitez que votre éditeur fournisse des vues de différents types. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], par exemple, fournit un mode formulaire et un mode Code.  
  
  Pour plus d’informations à ce sujet, consultez la procédure CreateEditorInstance dans le fichier EditorFactory.cs du projet de l’éditeur personnalisé créé par le modèle de package Visual Studio. Pour plus d’informations sur ce projet, consultez [procédure pas à pas : création d’un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Synchronisation des vues  
 Lorsque vous implémentez plusieurs vues, l’objet de données de document est chargé de conserver toutes les vues synchronisées avec les données. Vous pouvez utiliser les interfaces de gestion des événements sur <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> pour synchroniser plusieurs vues avec les données.  
  
 Si vous n’utilisez pas l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet pour synchroniser plusieurs vues, vous devez implémenter votre propre système d’événements pour gérer les modifications apportées à l’objet de données de document. Vous pouvez utiliser différents niveaux de granularité pour tenir à jour plusieurs vues. Avec un paramètre de granularité maximale, lorsque vous tapez dans une vue, les autres vues sont mises à jour immédiatement. Avec une granularité minimale, les autres vues ne sont pas mises à jour tant qu’elles ne sont pas activées.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Déterminer si les données du document sont déjà ouvertes  
 La table de document en cours d’exécution (RDT) dans l’environnement de développement intégré (IDE) permet de déterminer si les données d’un document sont déjà ouvertes, comme indiqué dans le diagramme suivant.  
  
 ![Graphique de DocDataView](../extensibility/media/docdataview.gif "DocDataView")  
Vues multiples  
  
 Par défaut, chaque vue (objet de vue de document) est contenue dans son propre cadre de fenêtre ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> ). Comme indiqué précédemment, toutefois, les données de document peuvent être affichées dans plusieurs vues. Pour ce faire, Visual Studio vérifie le RDT pour déterminer si le document en question est déjà ouvert dans un éditeur. Lorsque l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> pour créer l’éditeur, une valeur non null retournée dans le `punkDocDataExisting` paramètre indique que le document est déjà ouvert dans un autre éditeur. Pour plus d’informations sur la façon dont les fonctions RDT, consultez exécution de la [table de documents](../extensibility/internals/running-document-table.md).  
  
 Dans votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> implémentation, examinez l’objet de données de document retourné dans `punkDocDataExisting` pour déterminer si les données du document sont appropriées pour votre éditeur. (Par exemple, seules les données HTML doivent être affichées par un éditeur HTML.) Si cela est approprié, votre fabrique d’éditeur doit fournir une deuxième vue pour les données. Si le `punkDocDataExisting` paramètre n’est pas `NULL` , il est possible que l’objet de données du document soit ouvert dans un autre éditeur ou, plus vraisemblablement, que les données du document soient déjà ouvertes dans une vue différente avec l’éditeur. Si les données du document sont ouvertes dans un autre éditeur que votre fabrique d’éditeur ne prend pas en charge, Visual Studio ne parvient pas à ouvrir votre fabrique d’éditeur. Pour plus d’informations, consultez [Comment : attacher des vues à des données de document](../extensibility/how-to-attach-views-to-document-data.md).

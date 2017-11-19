---
title: Prend en charge plusieurs vues de Document | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79b9224a16388dabbe2b68553e5c0d9bfff29519
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="supporting-multiple-document-views"></a>Prend en charge plusieurs vues de Document
Vous pouvez fournir plusieurs vues d’un document en créant des données de document distinct et les objets de vue de document de votre éditeur. Certains cas dans lequel un affichage de document supplémentaire serait utile sont :  
  
-   Nouvelle prise en charge de la fenêtre : vous souhaitez que votre éditeur pour fournir plusieurs vues du même type, afin qu’un utilisateur qui possède déjà une fenêtre Ouvrir dans l’éditeur peut ouvrir une nouvelle fenêtre en sélectionnant le **nouvelle fenêtre** commande à partir de la **fenêtre** menu.  
  
-   Formulaire et le code de prise en charge afficher : vous souhaitez que votre éditeur pour proposer des vues de différents types. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], par exemple, fournit une vue de formulaire et un mode code.  
  
 Pour plus d’informations, consultez la procédure CreateEditorInstance dans le fichier EditorFactory.cs dans le projet de l’éditeur personnalisé créé par le modèle de Package Visual Studio. Pour plus d’informations sur ce projet, consultez [procédure pas à pas : création d’un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Synchronisation des vues  
 Lorsque vous implémentez plusieurs vues, l’objet de données de document est chargé de maintenir toutes les vues sont synchronisées avec les données. Vous pouvez utiliser sur des interfaces de gestion d’événements <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> à synchroniser plusieurs vues avec les données.  
  
 Si vous n’utilisez pas le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> objet synchroniser plusieurs vues, vous devez implémenter votre propre système d’événements pour gérer les modifications apportées à l’objet de données du document. Vous pouvez utiliser différents niveaux de granularité à plusieurs vues de mise à jour. Avec un paramètre de précision maximale, en cours de frappe dans une vue d’autres vues sont mis à jour immédiatement. Granularité minimale, autres vues ne sont pas mises à jour jusqu'à ce qu’ils sont activés.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Déterminer si des données du Document est déjà ouvert  
 La table du document en cours d’exécution (r & DT) dans l’environnement de développement intégré (IDE) permet de déterminer si les données d’un document sont déjà ouverts, comme indiqué dans le diagramme suivant.  
  
 ![Graphique de DocDataView](../extensibility/media/docdataview.gif "Docdataview")  
Vues multiples  
  
 Par défaut, chaque vue (objet de vue de document) est contenue dans le cadre de sa propre fenêtre (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). Comme déjà indiqué, toutefois, les données de document peuvent être affichées dans plusieurs vues. Pour activer cette option, Visual Studio vérifie la r & DT pour déterminer si le document en question est déjà ouvert dans un éditeur. Lorsque l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> pour créer l’éditeur, une valeur non NULL retournée dans le `punkDocDataExisting` paramètre indique que le document est déjà ouvert dans un autre éditeur. Pour plus d’informations sur les fonctions r & DT, consultez [Table de documents en cours d’exécution](../extensibility/internals/running-document-table.md).  
  
 Dans votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> mise en œuvre, examiner l’objet de données de document renvoyé dans `punkDocDataExisting` pour déterminer si les données du document sont adaptées à votre éditeur. (Par exemple, uniquement les données HTML doivent être affichées par un éditeur HTML.) Si cela est approprié, puis votre fabrique d’éditeur doit fournir une deuxième vue pour les données. Si le `punkDocDataExisting` paramètre n’est pas `NULL`, il est possible soit que l’objet de données de document est ouvert dans un autre éditeur ou, plus probable, que les données du document sont déjà ouverts dans une vue différente avec même l’éditeur. Si les données du document sont ouverts dans un autre éditeur votre fabrique d’éditeur ne prend pas en charge, Visual Studio ne parvient pas à ouvrir votre fabrique d’éditeur. Pour plus d’informations, consultez [Comment : joindre des vues à des données du Document](../extensibility/how-to-attach-views-to-document-data.md).
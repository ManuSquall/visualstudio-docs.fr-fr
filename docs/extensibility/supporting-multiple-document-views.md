---
title: Soutenir plusieurs points de vue sur les documents (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a952414fa7156d80675564e519e556ccedd524a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699537"
---
# <a name="supporting-multiple-document-views"></a>Prise en charge de vues de document multiples
Vous pouvez fournir plus d’une vue d’un document en créant des données de documents et des objets de vue de documents distincts pour votre éditeur. Certains cas où une vue supplémentaire des documents serait utile sont les :

- Nouveau support de fenêtre : Vous voulez que votre éditeur fournisse deux vues ou plus du même type, de sorte qu’un utilisateur qui a déjà une fenêtre ouverte dans l’éditeur puisse ouvrir une nouvelle fenêtre en sélectionnant la commande **De nouvelle fenêtre** du menu **Fenêtre.**

- Support de vue de formulaire et de code : Vous voulez que votre éditeur fournisse des vues de différents types. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], par exemple, fournit à la fois une vue de formulaire et une vue de code.

  Pour plus d’informations à ce sujet, voir la procédure CreateEditorInstance dans le fichier EditorFactory.cs dans le projet d’éditeur personnalisé créé par le modèle de paquet Visual Studio. Pour plus d’informations sur ce projet, voir [Procédure Pas à pas: Créer un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Synchronisation des vues
 Lorsque vous implémentez plusieurs vues, l’objet de données de document est responsable de la synchronisation de toutes les vues avec les données. Vous pouvez utiliser les interfaces de traitement de l’événement pour <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> synchroniser plusieurs vues avec les données.

 Si vous n’utilisez pas l’objet <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> pour synchroniser plusieurs vues, vous devez implémenter votre propre système d’événements pour gérer les modifications apportées à l’objet de données de document. Vous pouvez utiliser différents niveaux de granularité pour maintenir plusieurs vues à jour. Avec un réglage de granularité maximale, que vous tapez dans une vue les autres vues sont mises à jour immédiatement. Avec une granularité minimale, d’autres vues ne sont pas mises à jour jusqu’à ce qu’elles soient activées.

## <a name="determining-whether-document-data-is-already-open"></a>Déterminer si les données documentaires sont déjà ouvertes
 Le tableau de documents en cours d’exécution (RDT) dans l’environnement de développement intégré (IDE) permet de déterminer si les données d’un document sont déjà ouvertes, comme le montre le diagramme suivant.

 ![Graphique DocDataView](../extensibility/media/docdataview.gif "Docdataview (Docdataview)") Vues multiples

 Par défaut, chaque vue (objet de vue de<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>document) est contenue dans son propre cadre de fenêtre ( ). Toutefois, comme nous l’avons déjà mentionné, les données de documents peuvent être affichées dans plusieurs points de vue. Pour ce faire, Visual Studio vérifie le RDT pour déterminer si le document en question est déjà ouvert dans un éditeur. Lorsque l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> à créer l’éditeur, `punkDocDataExisting` une valeur non-NULL retournée dans le paramètre indique que le document est déjà ouvert dans un autre éditeur. Pour plus d’informations sur le fonctionnement du RDT, voir [Tableau des documents d’exécution](../extensibility/internals/running-document-table.md).

 Dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> votre implémentation, examinez l’objet de données documentaires `punkDocDataExisting` retournés pour déterminer si les données du document sont appropriées pour votre éditeur. (Par exemple, seules les données HTML doivent être affichées par un éditeur HTML.) Si cela est approprié, alors votre usine d’éditeur devrait fournir une deuxième vue pour les données. Si `punkDocDataExisting` le paramètre n’est pas, `NULL`il est possible soit que l’objet de données de document soit ouvert dans un autre éditeur, soit, plus probablement, que les données du document soient déjà ouvertes dans une vue différente avec le même éditeur. Si les données du document sont ouvertes dans un éditeur différent que votre usine d’éditeur ne prend pas en charge, alors Visual Studio ne parvient pas à ouvrir votre usine d’éditeur. Pour plus d’informations, voir [Comment : Joindre les vues aux données documentaires](../extensibility/how-to-attach-views-to-document-data.md).

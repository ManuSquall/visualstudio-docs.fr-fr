---
title: Tableau des documents en cours d’exécution (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e6aa882921786b1592922372581beae8c4c2443
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705565"
---
# <a name="running-document-table"></a>Exécution de la table de document
L’IDE tient la liste de tous les documents actuellement ouverts dans une structure interne appelée table de documents en cours d’exécution (RDT). Cette liste comprend tous les documents ouverts dans la mémoire, indépendamment du fait que ces documents sont actuellement en cours de modification. Un document est tout élément qui persiste, y compris les fichiers dans un projet ou le fichier principal du projet (par exemple, un fichier .vcxproj).

## <a name="elements-of-the-running-document-table"></a>Éléments de la table de documents de fonctionnement
 Le tableau de document en cours d’exécution contient les entrées suivantes.

|Élément|Description|
|-------------|-----------------|
|Surnom de document|Une chaîne qui identifie uniquement l’objet de données de document. Ce serait la voie de fichier absolue pour un système de projet qui gère les fichiers (par exemple, C: 'MyProject’MyFile). Cette chaîne est également utilisée pour les projets enregistrés dans des magasins autres que les systèmes de fichiers, tels que les procédures stockées dans une base de données. Dans ce cas, le système de projet peut inventer une chaîne unique qu’il peut reconnaître et éventuellement analyser pour déterminer comment stocker le document.|
|Propriétaire de la hiérarchie|L’objet hiérarchique qui possède <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> le document, représenté par une interface.|
|ID d’élément|Identifiant d’élément pour un élément spécifique dans la hiérarchie. Cette valeur est unique parmi tous les documents de la hiérarchie qui possède ce document, mais cette valeur n’est pas garantie d’être unique entre différentes hiérarchies.|
|Objet de données documentaires|Au minimum, il s’agit d’un`IUnknown`<br /><br /> . L’IDE ne nécessite pas `IUnknown` d’interface particulière au-delà de l’interface pour l’objet de données de document d’un éditeur personnalisé. Toutefois, pour un éditeur standard, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> mise en œuvre de l’interface par l’éditeur est nécessaire pour traiter les appels de persistance des fichiers du projet. Pour plus d’informations, voir [Enregistrer un document standard](../../extensibility/internals/saving-a-standard-document.md).|
|Indicateurs|Les indicateurs qui contrôlent si le document est enregistré, qu’un verrou de lecture ou de modification soit appliqué, et ainsi de suite, peuvent être spécifiés lorsque les entrées sont ajoutées au RDT. Pour plus d’informations, consultez l’énumération <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Modifier le nombre de serrures|Comptez des serrures de modification. Un verrou de modification indique qu’un éditeur a le document ouvert pour l’édition. Lorsque le nombre de verrous de modification passe à zéro, l’utilisateur est invité à enregistrer le document, s’il a été modifié. Par exemple, chaque fois que vous ouvrez un document dans un éditeur à l’aide de la commande **New Window,** un verrou de modification est ajouté pour ce document dans le RDT. Pour qu’un verrou de modification soit défini, le document doit avoir une carte d’identité de hiérarchie ou d’élément.|
|Lire Le compte de verrouillage|Comptez des serrures lues. Un verrou de lecture indique que le document est lu à travers un mécanisme tel qu’un assistant. Un verrou de lecture contient un document vivant dans le RDT tout en indiquant que le document ne peut pas être modifié. Vous pouvez définir un verrou de lecture même si le document n’a pas de hiérarchie ou d’id d’élément. Cette fonctionnalité vous permet d’ouvrir un document dans la mémoire et de l’entrer dans le RDT sans que le document soit détenu par aucune hiérarchie. Cette fonctionnalité est rarement utilisée.|
|Porte-serrure|Un exemple <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> d’interface. Le porte-serrure est implémenté par des fonctionnalités telles que les assistants qui ouvrent et modifient des documents en dehors d’un éditeur. Un porte-verrouillage permet à la fonction d’ajouter un verrou de modification au document pour empêcher la fermeture du document pendant qu’il est encore en cours de modification. Normalement, les serrures de modification ne sont ajoutées que par des fenêtres de documents (c’est-à-dire les éditeurs).|

 Chaque entrée dans le RDT a une hiérarchie unique ou id d’élément associé à elle, qui correspond généralement à un nœud dans le projet. Tous les documents disponibles pour l’édition appartiennent généralement à une hiérarchie. Entrées faites dans le contrôle RDT quel projet, ou, plus précisément, quelle hiérarchie, possède actuellement l’objet de données de document en cours de modification. En utilisant les informations contenues dans le RDT, l’IDE peut empêcher l’ouverture d’un document par plus d’un projet à la fois.

 La hiérarchie contrôle également la persistance des données et utilise les informations contenues dans le RDT pour mettre à jour les boîtes de dialogue **Save** and **Save As.** Lorsque les utilisateurs modifient un document puis choisissent la commande **de sortie** du menu **Fichier,** l’IDE les invite avec la boîte de dialogue **Save Changes** pour leur montrer tous les projets et les éléments de projet qui sont actuellement modifiés. Cela permet aux utilisateurs de choisir lequel des documents à enregistrer. La liste des documents à enregistrer (c’est-à-dire les documents qui ont des modifications) est générée à partir du RDT. Tous les éléments que vous vous attendez à voir dans la boîte de dialogue **Save Changes** à la sortie de l’application doivent avoir des enregistrements dans le RDT. Le RDT coordonne quels documents sont enregistrés et si l’utilisateur est invité à une opération d’enregistrement en utilisant les valeurs spécifiées dans l’entrée des drapeaux pour chaque document. Pour plus d’informations sur les <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> drapeaux du RDT, consultez le recensement.

## <a name="edit-locks-and-read-locks"></a>Modifier les serrures et lire les serrures
 Modifier les serrures et lire les serrures résident dans le RDT. La fenêtre de document incrémente et décrète la serrure de modification. Ainsi, lorsqu’un utilisateur ouvre une nouvelle fenêtre de document, le nombre de verrouillages de modification incréments par un. Lorsque le nombre de verrous de modification atteint zéro, la hiérarchie est signalée pour persister ou enregistrer les données pour le document associé. La hiérarchie peut alors persister les données de quelque manière que ce soit, y compris la persistance en tant que fichier ou comme élément dans un référentiel. Vous pouvez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> méthode dans l’interface pour ajouter <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> modifier les serrures et lire les serrures, et la méthode pour supprimer ces serrures.

 Normalement, lorsque la fenêtre de document d’un éditeur est instantanée, le cadre de la fenêtre ajoute automatiquement un verrou de modification pour le document dans le RDT. Toutefois, si vous créez une vue personnalisée d’un document qui n’utilise pas <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> une fenêtre de document standard (c’est-à-dire qu’elle ne met pas en œuvre l’interface), alors vous devez définir votre propre verrou de modification. Par exemple, dans un assistant, un document est édité sans être ouvert dans un éditeur. Pour que les verrous de documents soient ouverts par des sorciers <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> et des entités similaires, ces entités doivent implémenter l’interface. Pour enregistrer votre porte-verrouillage <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> de document, appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> la méthode et passez dans votre implémentation. Cela ajoute votre porte-verrouillage de document au RDT. Un autre scénario pour la mise en œuvre d’un porte-verrouillage de document est si vous ouvrez un document par une fenêtre d’outil spéciale. Dans ce cas, vous n’êtes pas en mesure d’avoir la fenêtre d’outil fermer le document. Toutefois, en vous inscrivant en tant que porte-verrou de document <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> dans le RDT, l’IDE peut appeler votre mise en œuvre de la méthode pour inciter une fermeture du document.

## <a name="other-uses-of-the-running-document-table"></a>Autres utilisations de la table de documents en cours d’exécution
 D’autres entités de l’IDE utilisent le RDT pour obtenir des renseignements sur les documents. Par exemple, le gestionnaire de contrôle source utilise le RDT pour dire au système de recharger un document dans l’éditeur, après qu’il obtienne la version la plus récente du fichier. Pour ce faire, le gestionnaire de contrôle source regarde les fichiers dans le RDT pour voir si l’un d’eux sont ouverts. Si c’est le cas, le gestionnaire de contrôle <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> source vérifie d’abord pour voir que la hiérarchie implémente la méthode. Si le projet ne <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> met pas en œuvre la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> méthode, le gestionnaire de contrôle source vérifie directement la mise en œuvre de la méthode sur l’objet de données du document.

 L’IDE utilise également le RDT pour refaire surface (apportez à l’avant) un document ouvert, si un utilisateur demande ce document. Pour plus d’informations, voir [Afficher les fichiers en utilisant la commande de fichiers ouverts](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Pour déterminer si un fichier est ouvert dans le RDT, faites-en un ce qui suit.

- Requête pour le surnom de document (c’est-à-dire le chemin complet du document) pour savoir si l’élément est ouvert.

- Utilisez la hiérarchie ou l’ID de l’élément pour demander au système de projet le chemin complet du document, puis regardez l’élément dans le RDT.

## <a name="see-also"></a>Voir aussi
- [Utilisation de RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Persistance et table de document en cours d’exécution](../../extensibility/internals/persistence-and-the-running-document-table.md)

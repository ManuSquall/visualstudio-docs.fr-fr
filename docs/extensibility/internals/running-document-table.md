---
title: Table de document en cours d’exécution | Microsoft Docs
description: Découvrez comment l’IDE de Visual Studio gère la table de document en cours d’exécution, qui comprend tous les documents ouverts en mémoire.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d260534d58853afc6b84ba484eb3a806250e2aa6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900406"
---
# <a name="running-document-table"></a>Exécution de la table de document
L’IDE gère la liste de tous les documents actuellement ouverts dans une structure interne appelée table de document en cours d’exécution (RDT). Cette liste comprend tous les documents ouverts en mémoire, que ces documents soient actuellement modifiés ou non. Un document est un élément qui est rendu persistant, y compris les fichiers d’un projet ou le fichier projet principal (par exemple, un fichier. vcxproj).

## <a name="elements-of-the-running-document-table"></a>Éléments de la table de document en cours d’exécution
 La table de document en cours d’exécution contient les entrées suivantes.

|Élément|Description|
|-------------|-----------------|
|Moniker de document|Chaîne qui identifie de façon unique l’objet de données de document. Il s’agit du chemin d’accès absolu d’un système de projet qui gère les fichiers (par exemple, C:\MyProject\MyFile). Cette chaîne est également utilisée pour les projets enregistrés dans des magasins autres que des systèmes de fichiers, tels que des procédures stockées dans une base de données. Dans ce cas, le système de projet peut inventer une chaîne unique qu’il peut reconnaître et éventuellement analyser pour déterminer comment stocker le document.|
|Propriétaire de la hiérarchie|Objet de hiérarchie qui possède le document, tel qu’il est représenté par une <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface.|
|ID de l’élément|Identificateur d’élément pour un élément spécifique dans la hiérarchie. Cette valeur est unique parmi tous les documents de la hiérarchie qui possède ce document, mais il n’est pas garanti que cette valeur soit unique dans différentes hiérarchies.|
|Objet de données de document|Au minimum, il s’agit d’un `IUnknown`<br /><br /> . L’IDE ne requiert pas d’interface particulière au-delà `IUnknown` de l’interface pour un objet de données de document de l’éditeur personnalisé. Toutefois, dans le cas d’un éditeur standard, l’implémentation de l’interface de l’éditeur <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> est requise pour gérer les appels de persistance du fichier à partir du projet. Pour plus d’informations, consultez [enregistrement d’un document standard](../../extensibility/internals/saving-a-standard-document.md).|
|Indicateurs|Indicateurs qui contrôlent si le document est enregistré, si un verrou de lecture ou de modification est appliqué, etc., peut être spécifié lors de l’ajout d’entrées à RDT. Pour plus d’informations, consultez l’énumération <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Modifier le nombre de verrous|Nombre de verrous de modification. Un verrou de modification indique que le document est ouvert dans un éditeur pour modification. Lorsque le nombre de verrous de modification passe à zéro, l’utilisateur est invité à enregistrer le document, s’il a été modifié. Par exemple, chaque fois que vous ouvrez un document dans un éditeur à l’aide de la commande **nouvelle fenêtre** , un verrou de modification est ajouté pour ce document dans le RDT. Pour que vous puissiez définir un verrou de modification, le document doit avoir un ID de hiérarchie ou d’élément.|
|Nombre de verrous en lecture|Nombre de verrous de lecture. Un verrou de lecture indique que le document est lu via un mécanisme comme un Assistant. Un verrou de lecture contient un document vivant dans le RDT tout en indiquant que le document ne peut pas être modifié. Vous pouvez définir un verrou de lecture même si le document n’a pas d’ID de hiérarchie ou d’élément. Cette fonctionnalité vous permet d’ouvrir un document en mémoire et de l’entrer dans le RDT sans que le document appartienne à une hiérarchie. Cette fonctionnalité est rarement utilisée.|
|Détenteur du verrou|Instance d’une <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interface. Le détenteur de verrou est implémenté par des fonctionnalités telles que des assistants qui ouvrent et modifient des documents en dehors d’un éditeur. Un détenteur de verrou permet à la fonctionnalité d’ajouter un verrou de modification au document pour empêcher la fermeture du document pendant qu’il est toujours en cours de modification. En règle générale, les verrous de modification sont ajoutés uniquement par les fenêtres de document (c’est-à-dire les éditeurs).|

 Chaque entrée de RDT a une hiérarchie unique ou un ID d’élément associé, qui correspond généralement à un nœud du projet. Tous les documents disponibles pour modification sont généralement détenus par une hiérarchie. Les entrées effectuées dans RDT contrôlent le projet, ou — plus précisément, la hiérarchie qui possède actuellement l’objet de données de document en cours de modification. À l’aide des informations contenues dans RDT, l’IDE peut empêcher l’ouverture d’un document par plusieurs projets à la fois.

 La hiérarchie contrôle également la persistance des données et utilise les informations de RDT pour mettre à jour les boîtes de dialogue **Enregistrer** et **Enregistrer sous** . Quand les utilisateurs modifient un document et qu’ils choisissent ensuite la commande **quitter** dans le menu **fichier** , l’IDE les affiche avec la boîte de dialogue **enregistrer les modifications** pour leur montrer tous les projets et éléments de projet actuellement modifiés. Cela permet aux utilisateurs de choisir les documents à enregistrer. La liste des documents à enregistrer (c’est-à-dire les documents qui ont été modifiés) est générée à partir du RDT. Tous les éléments que vous prévoyez d’afficher dans la boîte de dialogue **enregistrer les modifications** lors de la sortie de l’application doivent avoir des enregistrements dans le RDT. Le RDT coordonne les documents enregistrés et indique si l’utilisateur est invité à entrer une opération d’enregistrement à l’aide des valeurs spécifiées dans l’entrée Flags pour chaque document. Pour plus d’informations sur les indicateurs RDT, consultez l' <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> énumération.

## <a name="edit-locks-and-read-locks"></a>Modifier les verrous et les verrous de lecture
 Les verrous de modification et de lecture se trouvent dans le RDT. La fenêtre de document incrémente et décrémente le verrou de modification. Ainsi, lorsqu’un utilisateur ouvre une nouvelle fenêtre de document, le nombre de verrous de modification est incrémenté d’une unité. Lorsque le nombre de verrous de modification atteint zéro, la hiérarchie est signalée pour conserver ou enregistrer les données du document associé. La hiérarchie peut ensuite rendre les données persistantes d’une manière ou d’une autre, y compris les rendre persistantes sous la forme d’un fichier ou d’un élément dans un référentiel. Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> méthode dans l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interface pour ajouter des verrous de modification et des verrous de lecture, ainsi que la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> méthode pour supprimer ces verrous.

 Normalement, lorsque la fenêtre de document d’un éditeur est instanciée, le frame de fenêtre ajoute automatiquement un verrou de modification pour le document dans le RDT. Toutefois, si vous créez une vue personnalisée d’un document qui n’utilise pas une fenêtre de document standard (autrement dit, il n’implémente pas l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface), vous devez définir votre propre verrou de modification. Par exemple, dans un Assistant, un document est modifié sans être ouvert dans un éditeur. Pour que les verrous de document soient ouverts par des assistants et des entités similaires, ces entités doivent implémenter l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interface. Pour inscrire votre détenteur de verrou de document, appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> méthode et transmettez votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implémentation. Cela ajoute le détenteur de verrou de document à RDT. Un autre scénario pour l’implémentation d’un détenteur de verrou de document est que vous ouvrez un document à l’aide d’une fenêtre outil spéciale. Dans ce cas, vous ne pouvez pas faire en sorte que la fenêtre outil ferme le document. Toutefois, en s’inscrivant en tant que détenteur de verrou de document dans RDT, l’IDE peut appeler votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> méthode pour demander une fermeture du document.

## <a name="other-uses-of-the-running-document-table"></a>Autres utilisations de la table de document en cours d’exécution
 D’autres entités dans l’IDE utilisent RDT pour obtenir des informations sur les documents. Par exemple, le gestionnaire de contrôle de code source utilise RDT pour indiquer au système de recharger un document dans l’éditeur, après avoir obtenu la version la plus récente du fichier. Pour ce faire, le gestionnaire de contrôle de code source recherche les fichiers dans le RDT pour voir si l’un d’eux est ouvert. Si c’est le cas, le gestionnaire de contrôle de code source commence par vérifier que la hiérarchie implémente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> méthode. Si le projet n’implémente pas la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> méthode, le gestionnaire de contrôle de code source recherche directement une implémentation de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> méthode sur l’objet de données de document.

 L’environnement de développement intégré (IDE) utilise également le RDT pour résurfacer (amener à l’avant) un document ouvert, si un utilisateur demande ce document. Pour plus d’informations, consultez [affichage de fichiers à l’aide de la commande ouvrir un fichier](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Pour déterminer si un fichier est ouvert dans le RDT, effectuez l’une des opérations suivantes.

- Requête pour le moniker de document (autrement dit, le chemin d’accès complet au document) pour déterminer si l’élément est ouvert.

- Utilisez la hiérarchie ou l’ID d’élément pour demander au système de projet le chemin d’accès complet au document, puis recherchez l’élément dans le RDT.

## <a name="see-also"></a>Voir aussi
- [Utilisation de RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Persistance et table de document en cours d’exécution](../../extensibility/internals/persistence-and-the-running-document-table.md)

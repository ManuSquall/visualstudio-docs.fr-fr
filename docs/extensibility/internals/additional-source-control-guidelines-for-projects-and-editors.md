---
title: "Instructions de contrôle Source supplémentaires pour les projets et les éditeurs | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ee74f16c90dbf697732a490f895efb1a52233d80
ms.lasthandoff: 02/22/2017

---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Instructions de contrôle Source supplémentaires pour les projets et les éditeurs
Il existe un nombre de règles pour les projets et les éditeurs doivent respecter pour prendre en charge le contrôle de code source.  
  
## <a name="guidelines"></a>Recommandations  
 Votre projet ou votre éditeur de doit également effectuer les opérations suivantes pour prendre en charge le contrôle de code source :  
  
|Domaine|Projet|Éditeur|Détails|  
|----------|-------------|------------|-------------|  
|Copies des fichiers privés|x||L’environnement prend en charge les copies privées de fichiers. Autrement dit, chaque personne inscrite dans le projet a sa propre copie privée des fichiers dans le projet.|  
|Persistance de l’ANSI/Unicode|x|x|Si vous écrivez le code de persistance, conserver les fichiers dans le format ANSI, car la plupart des programmes de contrôle de code source ne prennent pas en charge Unicode.|  
|Énumérer les fichiers|x||Le projet doit contenir une liste spécifique de tous les fichiers qu’il contient et doit être en mesure d’énumérer la liste des fichiers à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child/Next_Sibling).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Le projet doit également exposer des noms d’élément via son <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>mise en œuvre et la prise en charge de la recherche de nom (y compris les fichiers spéciaux) via son <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>implémentation.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>|  
|Mise en forme|x|x|Dans la mesure du possible, les fichiers doivent être au format texte pour prendre en charge la fusion des différentes versions. Les fichiers qui ne sont pas au format texte ne peut pas être fusionnées ultérieurement avec d’autres versions du fichier. Le format de texte par défaut est XML.|  
|En fonction de référence|x||Projets basés sur les références sont facilement prises en charge dans le contrôle de code source. Toutefois, projets basés sur le répertoire sont également pris en charge par le contrôle de code source tant que le projet peut produire une liste de ses fichiers à la demande, quel que soit l’existent de ces fichiers sur le disque. Lorsque vous ouvrez un projet de contrôle de code source, le fichier projet est arrêté avant un de ses fichiers.|  
|Conserver les propriétés et les objets dans un ordre prévisible|x|x|Conserver vos fichiers dans un ordre prévisible, telles que l’ordre alphabétique, pour faciliter la fusion.|  
|Recharger|x|x|Lorsqu’un fichier change sur le disque, votre éditeur doit être en mesure de le recharger. Lorsque vous participez à contrôle de code source, l’environnement sera recharger les données pour vous en appelant votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>implémentation.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Le cas de recharger la plus difficile concerne une extraction se produit lorsque vous avez appelé IVsQueryEditQuerySave ::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et traitent des informations.</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Toutefois, votre code recharger doit être en mesure d’exécuter dans cette situation.<br /><br /> L’environnement recharge automatiquement les fichiers de projet. Toutefois, un projet doit implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>si elle est imbriquée pour prendre en charge le rechargement des hiérarchies imbriquées les fichiers projet.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge du contrôle de code Source](../../extensibility/internals/supporting-source-control.md)

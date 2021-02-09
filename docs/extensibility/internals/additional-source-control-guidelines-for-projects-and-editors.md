---
title: Instructions relatives au contrôle de code source pour les projets et les éditeurs
description: En savoir plus sur les instructions que les projets et les éditeurs doivent respecter pour prendre en charge le contrôle de code source.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 688c7de73c1a935ed6f7a30c6d956c7db97bdc6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906114"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Instructions supplémentaires sur le contrôle de code source pour les projets et les éditeurs
Pour prendre en charge le contrôle de code source, il existe un certain nombre d’instructions que les projets et les éditeurs doivent respecter.

## <a name="guidelines"></a>Consignes
 Votre projet ou éditeur doit également effectuer les opérations suivantes pour prendre en charge le contrôle de code source :

|Domaine|Project|Éditeur|Détails|
|----------|-------------|------------|-------------|
|Copies privées de fichiers|X||L’environnement prend en charge les copies privées des fichiers. Autrement dit, chaque personne inscrite dans le projet possède sa propre copie privée des fichiers dans ce projet.|
|Persistance ANSI/Unicode|X|X|Si vous écrivez le code de persistance, conservez les fichiers au format ANSI, car la plupart des programmes de contrôle de code source ne prennent pas en charge Unicode actuellement.|
|Énumérer les fichiers|X||Le projet doit contenir une liste spécifique de tous les fichiers qu’il contient et doit être en mesure d’énumérer la liste des fichiers à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Le projet doit également exposer les noms d’éléments via son <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> implémentation et la recherche de nom de prise en charge (y compris les fichiers spéciaux) par le biais de son <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implémentation.|
|Format Texte|X|X|Lorsque cela est possible, les fichiers doivent être au format texte pour prendre en charge la fusion de différentes versions. Les fichiers qui ne sont pas au format texte ne peuvent pas être fusionnés avec d’autres versions du fichier par la suite. Le format de texte par défaut est XML.|
|Basé sur la référence|X||Les projets basés sur la référence sont facilement pris en charge dans le contrôle de code source. Toutefois, les projets basés sur des répertoires sont également pris en charge par le contrôle de code source tant que le projet peut produire une liste de ses fichiers à la demande, que ces fichiers existent sur le disque ou non. Lors de l’ouverture d’un projet à partir du contrôle de code source, le fichier projet est d’abord arrêté avant l’un de ses fichiers.|
|Conserver les objets et les propriétés dans l’ordre prévisible|X|X|Rendez vos fichiers persistants dans un ordre prévisible, tel que l’ordre alphabétique, pour faciliter la fusion.|
|Recharger|X|X|Quand un fichier est modifié sur le disque, votre éditeur doit pouvoir le recharger. Lorsque vous participez au contrôle de code source, l’environnement recharge les données pour vous en appelant votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implémentation. Le cas de rechargement le plus difficile est lorsqu’une extraction se produit lorsque vous avez appelé IVsQueryEditQuerySave :: et que vous <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> traitez des informations. Toutefois, votre code de rechargement doit pouvoir s’exécuter dans cette situation.<br /><br /> L’environnement recharge automatiquement les fichiers projet. Toutefois, un projet doit implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> s’il possède des hiérarchies imbriquées afin de prendre en charge le rechargement des fichiers projet imbriqués.|

## <a name="see-also"></a>Voir aussi
- [Prendre en charge le contrôle de code source](../../extensibility/internals/supporting-source-control.md)

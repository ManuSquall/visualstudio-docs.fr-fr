---
title: Lignes directrices supplémentaires sur le contrôle des sources pour les projets et les rédacteurs en chef (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 181f6c10ff7ce95cd3a37151f117353d1bb47d41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710111"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Lignes directrices supplémentaires pour le contrôle des sources pour les projets et les éditeurs
Il existe un certain nombre de lignes directrices que les projets et les éditeurs devraient respecter afin de soutenir le contrôle des sources.

## <a name="guidelines"></a>Consignes
 Votre projet ou éditeur doit également faire ce qui suit pour soutenir le contrôle des sources :

|Domaine|Projet|Éditeur|Détails|
|----------|-------------|------------|-------------|
|Copies privées de fichiers|X||L’environnement prend en charge des copies privées de fichiers. Autrement dit, chaque personne enrôlée dans le projet a sa propre copie privée des dossiers dans ce projet.|
|Persistance ANSI/Unicode|X|X|Si vous écrivez le code de persistance, persistez les fichiers sous le formulaire ANSI parce que la plupart des programmes de contrôle source ne prennent pas actuellement en charge Unicode.|
|Énumérer les fichiers|X||Le projet doit contenir une liste spécifique de tous les fichiers qu’il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> contient <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> et doit être en mesure d’énumérer la liste des fichiers à l’aide de la ou (VSH_PROPID_First_Child/Next_Sibling). Le projet devrait également exposer <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> les noms d’objets par sa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> mise en œuvre et la recherche de noms de support (y compris les fichiers spéciaux) par sa mise en œuvre.|
|Format Texte|X|X|Dans la mesure du possible, les fichiers doivent être en format texte pour soutenir la fusion de différentes versions. Les fichiers qui ne sont pas en format texte ne peuvent pas être fusionnés avec d’autres versions du fichier plus tard. Le format texte préféré est XML.|
|Basé sur la référence|X||Les projets basés sur la référence sont facilement pris en charge dans le contrôle des sources. Toutefois, les projets basés sur l’annuaire sont également pris en charge par le contrôle des sources tant que le projet peut produire une liste de ses fichiers à la demande, peu importe si ces fichiers existent sur disque. Lors de l’ouverture d’un projet à partir du contrôle source, le fichier du projet est déposé d’abord avant l’un de ses fichiers.|
|Persévérer dans l’ordre prévisible|X|X|Persévérer dans un ordre prévisible, comme l’ordre alphabétique, pour faciliter la fusion.|
|Recharger|X|X|Lorsqu’un fichier change sur disque, votre éditeur doit être en mesure de le recharger. Lorsque vous participez au contrôle source, l’environnement <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> rechargera les données pour vous en appelant votre implémentation. Le cas de recharge le plus difficile est quand une caisse se produit lorsque<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> vous avez appelé IVsQueryEditQuerySave:: et traitent des informations. Cependant, votre code de recharge doit être en mesure de s’exécuter dans cette situation.<br /><br /> L’environnement recharge automatiquement les fichiers du projet. Cependant, un projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> doit être mis en œuvre s’il a imbriqué des hiérarchies afin de soutenir le rechargement des fichiers de projets imbriqués.|

## <a name="see-also"></a>Voir aussi
- [Contrôle des sources de soutien](../../extensibility/internals/supporting-source-control.md)

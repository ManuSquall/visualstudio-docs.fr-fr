---
title: "Syntaxe du chemin de domaine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine, chemin de domaine"
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 25
---
# Syntaxe du chemin de domaine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les définitions DSL utilisent une syntaxe semblable à XPath pour rechercher des éléments spécifiques dans un modèle.  
  
 En général, vous ne devez pas opérer sur cette syntaxe directement.  Quand elle apparaît dans la fenêtre Propriétés ou Détails DSL, vous pouvez cliquer sur la flèche vers le bas et utiliser l'éditeur de chemin d'accès.  Toutefois, le chemin d'accès apparaît dans ce format dans le champ une fois que vous avez utilisé l'éditeur.  
  
 Un chemin d'accès de domaine prend la forme suivante :  
  
 *Nom\_Relation.Nom\_Propriété\/\!Rôle*  
  
 ![Relation de référence CommentReferencesSubjects](../modeling/media/dsl_reference.png "dsl\_reference")  
  
 La syntaxe traverse l'arborescence du modèle.  Par exemple, la relation de domaine CommentReferencesSubjects dans l'illustration ci\-dessus a un rôle Subjects.  Le segment de chemin d'accès \/\!Subjects indique que le chemin d'accès se termine sur des éléments accessibles par l'intermédiaire du rôle Subjects.  
  
 Chaque segment commence par le nom d'une relation de domaine.  Si la traversée s'effectue à partir d'un élément vers une relation, le segment de chemin d'accès apparaît comme *Relation.Nom\_Propriété*.  Si le tronçon va d'un lien à un élément, le segment de chemin d'accès apparaît comme *Relation\/\!Nom\_Rôle*.  
  
 Les barres obliques séparent les différentes parties de la syntaxe d'un chemin d'accès.  Chaque segment de chemin d'accès est soit un tronçon d'un élément vers un lien \(une instance d'une relation\), soit un lien vers un élément.  Les segments de chemin d'accès apparaissent fréquemment par paires.  Un segment de chemin d'accès représente un tronçon d'un élément vers un lien et le segment suivant représente un tronçon du lien vers l'élément à l'autre extrémité.  \(Tout lien peut aussi être la source ou la cible d'une relation.\)  
  
 Le nom que vous utilisez pour le tronçon de l'élément vers le lien est la valeur de `Property Name` du rôle.  Le nom que vous utilisez pour le tronçon du lien vers l'élément est le nom du rôle cible.  
  
## Voir aussi  
 [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md)
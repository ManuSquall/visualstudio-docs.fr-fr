---
title: "La syntaxe du chemin d’accès au domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain path
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: fb2b1dfa13bf00c29452798253198b2ad0e72e97
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="domain-path-syntax"></a>Syntaxe du chemin de domaine
Les définitions DSL utilisent une syntaxe semblable à XPath pour rechercher des éléments spécifiques dans un modèle.  
  
 En général, vous ne devez pas opérer sur cette syntaxe directement. Quand elle apparaît dans la fenêtre Propriétés ou Détails DSL, vous pouvez cliquer sur la flèche vers le bas et utiliser l'éditeur de chemin d'accès. Toutefois, le chemin d'accès apparaît dans ce format dans le champ une fois que vous avez utilisé l'éditeur.  
  
 Un chemin d'accès de domaine prend la forme suivante :  
  
 *RelationshipName.PropertyName/!Role*  
  
 ![Relation de référence CommentReferencesSubjects](../modeling/media/dsl_reference.png "dsl_reference")  
  
 La syntaxe traverse l'arborescence du modèle. Par exemple, la relation de domaine **CommentReferencesSubjects** dans l’illustration ci-dessus a un **sujets** rôle. Le segment de chemin d’accès **/ ! Subjectt** Spécifie que le chemin d’accès se termine sur les éléments accédées par le biais du **sujets** rôle.  
  
 Chaque segment commence par le nom d'une relation de domaine. Si le parcours provient d’un élément à une relation, le segment de chemin d’accès s’affiche en tant que *Relationship.PropertyName*. Si le saut est à partir d’un lien à un élément, le segment de chemin d’accès s’affiche en tant que *relation / ! RoleName*.  
  
 Les barres obliques séparent les différentes parties de la syntaxe d'un chemin d'accès. Chaque segment de chemin d'accès est soit un tronçon d'un élément vers un lien (une instance d'une relation), soit un lien vers un élément. Les segments de chemin d'accès apparaissent fréquemment par paires. Un segment de chemin d'accès représente un tronçon d'un élément vers un lien et le segment suivant représente un tronçon du lien vers l'élément à l'autre extrémité. (Tout lien peut aussi être la source ou la cible d'une relation.)  
  
 Le nom que vous utilisez pour le tronçon de l'élément vers le lien est la valeur de `Property Name` du rôle. Le nom que vous utilisez pour le tronçon du lien vers l'élément est le nom du rôle cible.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md)
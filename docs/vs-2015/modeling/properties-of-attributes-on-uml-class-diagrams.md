---
title: Propriétés d’attributs sur UML des diagrammes de classes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 27affdb42f6f5ad1dd4c880b87e3cbf737d52921
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948060"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>Propriétés d’attributs dans des diagrammes de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un diagramme de classes UML, vous pouvez ajouter des *attributs* aux classes et interfaces. Un attribut définit des valeurs qui peuvent être associées à des instances de la classe ou de l’interface.  

 Pour ajouter un attribut, cliquez avec le bouton droit sur la classe ou l’interface, pointez sur **Ajouter**, puis cliquez sur **Attribut**.  

 Si les attributs d’une classe ne sont pas visibles sur le diagramme, cliquez sur le chevron situé en haut de la classe ou de l’interface pour la développer. Si l’en-tête **Attributs** est visible, cliquez sur **[+]** pour développer la section des attributs.  

## <a name="signature-of-an-attribute"></a>Signature d’un attribut  
 La signature d’un attribut correspond à la ligne qui le représente dans une classe ou une interface dans un diagramme de classes UML. Sa forme est la suivante :  

```  
+ AttributeName : TypeName [*]  
```  

 \+ Indique une visibilité publique. Les autres valeurs autorisées sont - (privé), # (protégé), ~ (package).  

 `AttributeName` est souligné si l’attribut est statique.  

 `: TypeName` est omis si l’attribut n’a aucun type.  

 `[*]` indique la multiplicité. Il est omis si la multiplicité est de 1.  

## <a name="properties"></a>Properties  
 Le tableau suivant décrit les propriétés d’un attribut dans une classe ou une interface dans un diagramme de classes UML.  

 Pour afficher les propriétés d’un attribut, cliquez avec le bouton droit sur l’attribut dans la classe ou l’interface sur le diagramme, puis cliquez sur **Propriétés**. Les propriétés s’affichent dans la fenêtre Propriétés.  

 Pour afficher les propriétés d’un attribut, cliquez avec le bouton droit dessus, puis cliquez sur **Propriétés**.  


|   **Property**    | **Default**  |                                                                                                                                                                                                         Description                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Valeur par défaut** |   (vide)    |                                                                                                                                                                               Valeur de l’attribut quand le classifieur est instancié.                                                                                                                                                                                |
| **Est en lecture seule**  |    False     |                                                                                                                                                                                    Si la valeur est true, la valeur de l’attribut ne peut pas être modifiée.                                                                                                                                                                                    |
|   **Est statique**   |    False     |                                                                                                                    Si la valeur est true, une valeur unique pour cet attribut est partagée entre toutes les instances de ce type.<br /><br /> Si la valeur est true, le nom de l’attribut est souligné là où il apparaît sur le diagramme.                                                                                                                    |
|     **Name**      | (un nouveau nom) |                                                                                                                                                                                        Doit être unique dans le classifieur propriétaire.                                                                                                                                                                                        |
|     **Type**      |    (aucune)    |                                                Type primitif, comme **Entier**, ou type défini dans le modèle. Vous ne pouvez pas utiliser des types non primitifs comme **Décimal** , car la valeur doit être encodée dans les métadonnées. Si vous entrez un nom pour un nouveau type dans cette propriété, un type est ajouté à la section **Types non spécifiés** de l’Explorateur de modèles UML.                                                 |
|  **Visibilité**   |    Public    |                                     Les valeurs autorisées et les caractères qui apparaissent dans la signature sont les suivants :<br /><br /> **+ Public** - visible globalement<br /><br /> **- Privé** : non visible en dehors du type propriétaire<br /><br /> **# Protégé** : visible pour les types dérivés du propriétaire<br /><br /> **~ Package** : visible pour d’autres types au sein du même package                                      |
|  **Éléments de travail**   | {0} associé |                                                                                                                          Nombre d’éléments de travail associés. Lecture seule.<br /><br /> Pour plus d’informations, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).                                                                                                                           |
|    **Est une feuille**    |    False     |                                                                                                                                                                    Si la valeur est true, l’autorisation de la redéfinition de cet attribut dans les types dérivés n’est pas prévue.                                                                                                                                                                     |
|  **Est dérivée**   |    False     |                                                                                                              Si la valeur est true, cet attribut est calculé à partir d’autres attributs. Par exemple, l’attribut Diagonal est calculé à partir de la largeur et la hauteur. Les détails doivent être écrits dans **Description** ou dans un commentaire associé.                                                                                                              |
|  **Description**  |   (vide)    |                                                                                                                                                                        Pour des remarques générales ou pour définir des contraintes sur les valeurs dans l’attribut.                                                                                                                                                                        |
| **Multiplicité**  |      1       | **1** - cet attribut a une valeur unique du type spécifié.<br /><br /> **0..1** - cet attribut peut avoir la valeur `null`.<br /><br /> **\\**\* -valeur de cet attribut est une collection de valeurs.<br /><br /> **1..\\**  \* -valeur de cet attribut est une collection qui contient au moins une valeur.<br /><br /> *n* **..** *m* - la valeur de cet attribut est une collection qui contient entre *n* et *m* valeurs. |
|  **Est ordonné**   |    False     |                                                                                                                                                                    Si la valeur est true, la collection forme une liste séquentielle. Pour une valeur **Multiplicité** supérieure à 1.                                                                                                                                                                     |
|   **Est unique**   |    False     |                                                                                                                                                                Si la valeur est true, la collection ne contient pas de valeur en double. Pour une valeur **Multiplicité** supérieure à 1.                                                                                                                                                                |

## <a name="see-also"></a>Voir aussi  
 [Diagrammes de classes UML : Référence](../modeling/uml-class-diagrams-reference.md)   
 [Propriétés de types de diagrammes de classes UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Propriétés d’opérations sur les diagrammes de classes UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Diagrammes de classes UML : Instructions](../modeling/uml-class-diagrams-guidelines.md)   
 [Diagrammes de classes UML : Recommandations](../modeling/uml-class-diagrams-guidelines.md)

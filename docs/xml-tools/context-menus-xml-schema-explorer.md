---
title: "Menus contextuels (Explorateur de sch&#233;mas XML) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Menus contextuels (Explorateur de sch&#233;mas XML)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les éléments de menu contextuel suivants vous permettent d'effectuer des recherches spécifiques au schéma et d'autres opérations.  
  
## Type de nœud : jeu de schémas  
 Le tableau suivant décrit les options disponibles pour un nœud de type jeu de schémas.  
  
|Option|Description|  
|------------|-----------------|  
|**Afficher les éléments racines les plus probables**|Recherche et met en surbrillance tous les éléments globaux qui ne sont pas référencés à partir d'éléments globaux autres qu'eux\-mêmes.|  
|**Afficher les types globaux**|Recherche et met en surbrillance tous les types globaux dans le jeu de schémas.|  
|**Afficher les éléments globaux**|Recherche et met en surbrillance tous les éléments globaux dans le jeu de schémas.|  
|**Fenêtre Propriétés**|Ouvre la fenêtre **Propriétés** \(si elle n'est pas déjà ouverte\).Cette fenêtre affiche des informations sur le nœud.|  
  
## Type de nœud : espace de noms  
 Le tableau suivant décrit les options disponibles pour un nœud de type espace de noms.  
  
|Option|Description|  
|------------|-----------------|  
|**Afficher toutes les références entrantes**|Recherche et met en surbrillance les fichiers qui importent l'espace de noms sélectionné.|  
|**Afficher toutes les références sortantes**|Pour chaque fichier de l'espace de noms sélectionné, recherche et met en surbrillance les éléments suivants :<br /><br /> -   tous les espaces de noms référencés dans des instructions import sans attribut `schemaLocation` ;<br />-   tous les fichiers contenus dans les espaces de noms autres que l'espace de noms sélectionné, et qui sont spécifiés dans l'attribut `schemaLocation` des instructions import et include.|  
|**Afficher les types globaux**|Recherche et met en surbrillance tous les types globaux dans l'espace de noms sélectionné.|  
|**Afficher les éléments globaux**|Recherche et met en surbrillance tous les éléments globaux dans l'espace de noms sélectionné.|  
|**Fenêtre Propriétés**|Ouvre la fenêtre **Propriétés** \(si elle n'est pas déjà ouverte\).Cette fenêtre affiche des informations sur le nœud.|  
  
## Type de nœud : fichier  
 Le tableau suivant décrit les options disponibles pour un nœud de type fichier.  
  
|Option|Description|  
|------------|-----------------|  
|**Afficher toutes les références entrantes**|Recherche et met en surbrillance tous les fichiers qui spécifient le fichier sélectionné dans les attributs `schemaLocation` de leurs instructions include et import.|  
|**Afficher toutes les références sortantes**|Recherche et met en surbrillance les éléments suivants :<br /><br /> -   tous les espaces de noms spécifiés dans les attributs d'espaces de noms de toutes les instructions import qui n'ont pas l'attribut `schemaLocation` ;<br />-   tous les fichiers spécifiés dans les attributs `schemaLocation` de toutes les instructions import et include.|  
|**Afficher les types globaux**|Recherche et met en surbrillance tous les types globaux dans ce fichier.|  
|**Afficher les éléments globaux**|Recherche et met en surbrillance tous les éléments globaux dans ce fichier.|  
|**Afficher le code**|Ouvre le fichier qui contient le nœud sélectionné dans l'Éditeur XML.L'élément sélectionné dans l'Explorateur de schémas XML est également sélectionné dans l'Éditeur XML.|  
|**Fenêtre Propriétés**|Ouvre la fenêtre **Propriétés** \(si elle n'est pas déjà ouverte\).Cette fenêtre affiche des informations sur le nœud.|  
  
## Tous les types de nœuds globaux  
 Le tableau suivant décrit les options disponibles pour tous les nœuds globaux.  
  
|Option|Description|  
|------------|-----------------|  
|**Afficher dans la vue du graphique**|Ouvre la vue du graphique.Si le nœud sélectionné n'est pas dans l'espace de travail, ajoute ce nœud à l'espace de travail et sélectionne le nœud.|  
|**Afficher dans la vue de modèle de contenu**|Ouvre la vue de modèle de contenu.Si le nœud sélectionné n'est pas dans l'espace de travail, ajoute ce nœud à l'espace de travail et sélectionne le nœud.|  
|**Afficher le code**|Ouvre le fichier qui contient le nœud sélectionné dans l'Éditeur XML.L'élément sélectionné dans l'Explorateur de schémas XML est également sélectionné dans l'Éditeur XML.|  
|**Fenêtre Propriétés**|Ouvre la fenêtre **Propriétés** \(si elle n'est pas déjà ouverte\).Cette fenêtre affiche des informations sur le nœud.|  
  
## Type de nœud : élément  
 En plus des options relatives aux nœuds globaux décrites ci\-dessus, le menu contextuel pour les nœuds d'élément comprend les options suivantes :  
  
|Option|Description|  
|------------|-----------------|  
|**Aller à la définition de type**|Navigue vers la définition de type de l'élément sélectionné.Ceci s'applique lorsque le type utilisé pour l'élément est un type global.|  
|**Aller à l'élément d'origine**|Pour les références d'élément, navigue vers la définition réelle de l'élément.|  
|**Afficher toutes les références**|Pour les éléments globaux, recherche et met en surbrillance toutes les références \(éléments qui ont `ref="selectedElement"`\) à l'élément sélectionné.|  
|**Afficher les membres du groupe de substitution**|Pour les en\-têtes d'un groupe de substitution, recherche et met en surbrillance tous les éléments qui sont membres du groupe de substitution dont l'élément sélectionné est membre.Cela permet d'afficher les participants directs et indirects.|  
|**Afficher les en\-têtes du groupe de substitution**|Pour les éléments globaux qui sont membres d'un groupe de substitution, recherche et met en surbrillance tous les en\-têtes directs et indirects de l'élément sélectionné, notamment :<br /><br /> -   en\-tête de groupe de substitution spécifié sur l'élément sélectionné ;<br />-   en\-tête de groupe de substitution spécifié sur son élément d'en\-tête.|  
|**Générer un exemple de code XML**|Disponible uniquement pour les éléments globaux.Génère un exemple de fichier XML pour l'élément global.|  
  
## Type de nœud : types globaux  
 En plus des options relatives aux nœuds globaux décrites ci\-dessus, le menu contextuel pour les nœuds de type global comprend les options suivantes :  
  
|Option|Description|  
|------------|-----------------|  
|**Afficher le type de base**|Si le type sélectionné est dérivé d'un type global, navigue vers le type de base du type sélectionné.|  
|**Afficher toutes les références**|Recherche et met en surbrillance toutes les références au type sélectionné.Ceci inclut les éléments et attributs du type sélectionné ainsi que les types dérivés du type sélectionné.|  
|**Afficher tous les types dérivés**|Recherche et met en surbrillance tous les types qui sont directement et indirectement dérivés du type sélectionné.|  
|**Afficher tous les ancêtres**|Affiche tous les types parents \(de base\).|  
  
## Type de nœud : attribut  
 En plus des options relatives aux nœuds globaux décrites ci\-dessus, le menu contextuel pour les nœuds d'attribut comprend les options suivantes :  
  
|Option|Description|  
|------------|-----------------|  
|**Aller à la définition de type**|Lorsque le type utilisé pour l'attribut est un type global, navigue vers la définition de type de l'attribut sélectionné.|  
|**Aller à l'attribut d'origine**|Pour les références d'attribut, navigue vers la définition réelle de l'attribut.|  
|**Afficher toutes les références**|Pour les attributs globaux, recherche et met en surbrillance toutes les références \(autres attributs qui ont `ref="selectedAttribute"`\) à l'attribut sélectionné.|  
  
## Type de nœud : groupe d'attributs  
 En plus des options relatives aux nœuds globaux décrites ci\-dessus, le menu contextuel pour les nœuds d'attribut comprend les options suivantes :  
  
|Option|Description|  
|------------|-----------------|  
|**Aller à la définition**|Pour les références, navigue vers la définition réelle de l'attribut.|  
|**Afficher tous les membres**|Recherche et met en surbrillance tous les membres du groupe d'attributs.|  
|**Afficher toutes les références**|Recherche et met en surbrillance toutes les références \(groupes d'attributs qui ont `ref="selectedAttributeGroup"`\) au groupe d'attributs sélectionné.|  
  
## Type de nœud : groupe nommé  
 En plus des options relatives aux nœuds globaux décrites ci\-dessus, le menu contextuel pour les nœuds de groupe nommé comprend les options suivantes :  
  
|Option|Description|  
|------------|-----------------|  
|**Aller à la définition**|Pour les références, navigue vers la définition réelle de l'attribut.|  
|**Afficher tous les membres**|Recherche et met en surbrillance tous les membres du groupe nommé.|  
|**Afficher toutes les références**|Recherche et met en surbrillance toutes les références \(groupes qui ont `ref="selectedGroup"`\) au groupe sélectionné.|  
  
## Voir aussi  
 [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md)   
 [Recherche dans le jeu de schémas](../xml-tools/searching-the-schema-set.md)
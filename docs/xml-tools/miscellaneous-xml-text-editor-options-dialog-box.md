---
title: "Divers, XML, &#201;diteur de texte, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Divers, XML, &#201;diteur de texte, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue permet de modifier les paramètres de saisie semi\-automatique et de schéma de l'éditeur XML.Vous pouvez accéder à la boîte de dialogue **Options** à partir du menu **Outils**.  
  
> [!NOTE]
>  Ces paramètres ne sont disponibles que lorsque vous sélectionnez les dossiers **Éditeur de texte** et **XML**, puis l'option **Divers** dans la boîte de dialogue **Options**.  
  
## Insertion automatique  
 **Balises de fermeture**  
 Si le paramètre de saisie semi\-automatique est sélectionné, l'éditeur ajoute automatiquement une balise de fin lorsque vous tapez un crochet pointu droit \(\>\) pour fermer une balise de début, si la balise n'est pas déjà fermée.Il s'agit du comportement par défaut.  
  
 La saisie d'un élément vide ne dépend pas du paramètre de saisie semi\-automatique.Vous pouvez toujours effectuer la saisie semi\-automatique d'un élément vide en tapant une barre oblique inverse \(\/\).  
  
 **Guillemets d'attribut**  
 Lorsque vous éditez des attributs XML, l'éditeur insère les caractères `=" "` et place le signe ^ à l'intérieur des guillemets doubles.  
  
 Cette option est sélectionnée par défaut.  
  
 **Déclarations d'espaces de noms**  
 L'éditeur insère automatiquement des déclarations d'espaces de noms chaque fois qu'elles sont nécessaires.  
  
 Cette option est sélectionnée par défaut.  
  
 **Autre balisage \(commentaires, CDATA\)**  
 Les commentaires, CDATA, DOCTYPE, instructions de traitement et autres balisages sont automatiquement complétés.  
  
 Cette option est sélectionnée par défaut.  
  
## Réseau  
 **Télécharger automatiquement les DTD et les schémas**  
 Les schémas et les DTD \(définitions de type de document\) sont automatiquement téléchargés à partir d'emplacements HTTP.Cette fonction utilise System.Net avec la détection automatique de serveur proxy activée.  
  
 Cette option est sélectionnée par défaut.  
  
## Mode plan  
 **Passer en mode Plan à l'ouverture des fichiers**  
 Active le mode plan à l'ouverture d'un fichier.  
  
 Cette option est sélectionnée par défaut.  
  
## Mise en cache  
 **Schémas**  
 Spécifie l'emplacement du cache de schéma.Le bouton Parcourir \(**...**\) permet d'ouvrir la boîte de dialogue **Parcourir les répertoires** à l'emplacement actuel du cache de schéma.Vous pouvez sélectionner un autre répertoire ou sélectionner un dossier dans la boîte de dialogue, puis cliquer avec le bouton droit et choisir **Ouvrir** pour afficher le contenu de ce répertoire.  
  
## Voir aussi  
 [Propriétés des documents XML, fenêtre Propriétés](../xml-tools/xml-document-properties-properties-window.md)   
 [Composants de l'éditeur XML](../xml-tools/xml-editor-components.md)
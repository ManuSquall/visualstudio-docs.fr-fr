---
title: "Bo&#238;te de dialogue Sch&#233;mas XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Bo&#238;te de dialogue Sch&#233;mas XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La boîte de dialogue **Schémas XML** permet de sélectionner le schéma de langage XSD \(XML schema definition\) à associer à un document XML.Vous pouvez sélectionner un schéma dans le cache de schéma ou spécifier un schéma situé ailleurs dans le cache.Les schémas sélectionnés sont considérés comme faisant partie d'un jeu de schémas.Le jeu de schémas est utilisé pour IntelliSense et pour la validation de documents XML.  
  
 Pour accéder à la boîte de dialogue **Schémas XML**, cliquez sur le bouton **Schémas** de la fenêtre des propriétés du document, ou sélectionnez **Schémas** dans le menu **XML**.  
  
## Liste UIElement  
 **Utilisation**  
 Sélectionnez la manière dont le schéma XML doit être utilisé.  
  
-   **Automatique**.Ce schéma n'est pas utilisé par le document en cours mais est disponible pour l'association automatique.Si le document XML déclare un espace de noms qui correspond au `targetNamespace` de ce schéma, le schéma sera automatiquement associé et inclus dans le jeu de schémas.  
  
-   **Utiliser ce schéma** .Ce schéma est utilisé par le document en cours.Soit l'utilisateur a explicitement demandé que ce schéma soit utilisé en cliquant sur cette colonne, soit le schéma a été automatiquement associé en fonction d'un `targetNamespace` correspondant.  
  
-   **Ne pas utiliser les schémas sélectionnés**.Ce schéma n'est pas utilisé par le document actif, même si le schéma a un `targetNamespace` correspondant.Ce paramètre peut être utile dans la résolution de conflits, lorsqu'il existe plusieurs versions du même schéma dans le cache de schéma ou dans la solution.  
  
 **Espace de noms cible**  
 Affiche l'espace de noms cible associé au schéma XML.  
  
 **Nom de fichier**  
 Affiche le nom de fichier du schéma XML.  
  
 **Ajouter**  
 Permet d'ouvrir la boîte de dialogue **Ouvrir le schéma XSD** pour que vous sélectionniez d'autres schémas à ajouter au jeu de schémas.Lorsque vous ajoutez un schéma au jeu de schémas, la valeur de la colonne **Utiliser** est **Utiliser ce schéma**.  
  
 **Supprimer**  
 Supprime le schéma actuellement sélectionné du jeu de schémas.Cela supprime le schéma du cache de schémas en mémoire, mais pas du système de fichiers.  
  
## Voir aussi  
 [Composants de l'éditeur XML](../xml-tools/xml-editor-components.md)   
 [Procédure : sélectionner les schémas XML à utiliser](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [Cache de schéma](../xml-tools/schema-cache.md)
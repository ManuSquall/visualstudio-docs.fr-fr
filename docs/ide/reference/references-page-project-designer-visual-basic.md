---
title: "Page R&#233;f&#233;rences, Concepteur de projets (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesReference"
  - "vb.ProjectPropertiesUnusedReference"
  - "vb.ProjectPropertiesReferencePaths"
helpviewer_keywords: 
  - "Page Références dans le Concepteur de projets"
  - "Concepteur de projets, page Références"
  - "Références inutilisées, boîte de dialogue"
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Page R&#233;f&#233;rences, Concepteur de projets (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisez la page **Références** du **Concepteur de projets** pour gérer des références, des références Web et des espaces de noms importés dans votre projet.  Les projets peuvent contenir des références aux composants COM, des services Web XML, des bibliothèques de classes ou assemblys .NET Framework ou d'autres bibliothèques de classes.  Pour plus d'informations sur l'utilisation des références, consultez [Gestion des références dans un projet](../../ide/managing-references-in-a-project.md).  
  
 Pour accéder à la page **Références**, sélectionnez un nœud de projet \(pas le nœud **Solution** \) dans **Explorateur de solutions**.  Choisissez **Projet**, **Propriétés** dans la barre de menus.  Lorsque le Concepteur de projets s'affiche, cliquez sur **Références** tableau.  
  
## Liste UIElement  
 Les options suivantes vous permettent de sélectionner ou de supprimer des références et des espaces de noms importés dans votre projet.  
  
 **Références inutilisées**  
 Cliquez sur ce bouton pour accéder à la boîte de dialogue **Références inutilisées** .  
  
 La boîte de dialogue **Références inutilisées** vous permet de supprimer des références incluses dans votre projet sans être réellement utilisées par le code.  Il contient une grille qui répertorie **Nom de la référence**, **Chemin d'accès**, et d'autres informations sur les références d'espace de noms inutilisées dans votre projet.  Dans la grille, sélectionnez les références d'espaces de noms que vous souhaitez supprimer de votre projet, puis cliquez sur **Supprimer**.  
  
 **Chemins d'accès des références**  
 Cliquez sur ce bouton pour accéder à la boîte de dialogue **Chemins d'accès des références** .  
  
> [!NOTE]
>  Lorsque le système de projet recherche une référence d'assembly, le système résout la référence en consultant les emplacements suivants, dans l'ordre suivant :  
>   
>  1.  Le dossier du projet.  Les fichiers du dossier du projet s'affichent dans **Explorateur de solutions** lorsque **Afficher tous les fichiers** n'est pas appliquée.  
> 2.  Les dossiers spécifiés dans la boîte de dialogue **Chemins d'accès des références** .  
> 3.  Dossiers qui affichent des fichiers dans la boîte de dialogue **Ajouter une référence** .  
> 4.  Le dossier obj du projet.  \(Lorsque vous ajoutez une référence COM à votre projet, un ou plusieurs assemblys peuvent être ajoutés au dossier obj du projet.\)  
  
 **Références**  
 Cette liste affiche toutes les références dans le projet, utilisées ou inutilisées.  
  
 **Ajouter**  
 Cliquez sur ce bouton pour ajouter une référence ou référence Web à la liste **Références**.  
  
 Choisissez **Référence** pour ajouter une référence à votre projet à l'aide de la boîte de dialogue Ajouter une référence.  
  
 Choisissez **Référence Web** pour ajouter une référence Web à votre projet à l'aide de la boîte de dialogue Ajouter une référence Web.  
  
 **Supprimer**  
 Sélectionnez une ou plusieurs références dans la liste **Références**, puis cliquez sur ce bouton pour la supprimer.  
  
 **Mettre à jour la référence Web**  
 Sélectionnez une référence Web dans la liste **Références** et cliquez sur ce bouton pour la mettre à jour.  
  
 **Espaces de noms importés**  
 Vous pouvez taper votre propre espace de noms dans cette zone et cliquer sur **Ajouter une importation utilisateur** pour l'ajouter à la liste d'espaces de noms.  
  
 Vous pouvez créer des alias pour les espaces de noms importés par l'utilisateur.  Pour cela, entrez l'alias et l'espace de noms selon le format *alias*\=*EspaceNoms*..  Ceci est utile si vous utilisez de longs espaces de noms, par exemple : `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.  
  
 **Ajouter une importation utilisateur**  
 Cliquez sur ce bouton pour ajouter l'espace de noms spécifié dans la zone **Espaces de noms importés** à la liste des espaces de noms importés.  Le bouton n'est actif que si l'espace de noms spécifié ne figure pas déjà dans la liste.  
  
 **List d'espaces de noms**  
 Cette liste affiche tous les espaces de noms disponibles.  Les cases à cocher pour les espaces de noms inclus dans votre projet sont activées.  
  
 **Mettre à jour l'import utilisateur**  
 Sélectionnez un espace de noms défini par l'utilisateur dans la liste d'espaces de noms, tapez un nouveau nom pour cet espace dans la zone **Espaces de noms importés**, puis cliquez sur ce bouton pour valider le nouvel espace de noms.  Le bouton n'est actif que si l'espace de noms sélectionné est l'un de ceux que vous avez ajouté à la liste à l'aide du bouton **Ajouter une importation utilisateur**.  vous pouvez ajouter :  
  
-   Des classes ou des espaces de noms, tels que <xref:System.Math?displayProperty=fullName>.  
  
-   Des importations avec alias, telles que `VB=Microsoft.VisualBasic`.  
  
-   Des espaces de noms XML, tels que `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.  
  
## Voir aussi  
 [Comment : ajouter ou supprimer des références à l'aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Comment : ajouter ou supprimer des espaces de noms importés \(Visual Basic\)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)   
 [NIB: Add Web Reference Dialog Box](http://msdn.microsoft.com/fr-fr/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [Imports Statement \(XML Namespace\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
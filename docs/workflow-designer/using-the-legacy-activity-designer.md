---
title: "Utilisation du concepteur d&#39;activit&#233;s h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "activités, ajout d'un élément enfant"
  - "activités, configuration"
  - "activités, créer, personnalisées"
  - "concepteur d'activités"
  - "activités enfants, ajout"
  - "activités personnalisées"
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Utilisation du concepteur d&#39;activit&#233;s h&#233;rit&#233;
Cette rubrique décrit comment utiliser le concepteur d'activités dans le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité.Utilisez le concepteur hérité lorsque vous ciblez le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Le concepteur d'activités vous permet de créer vos propres activités personnalisées.  
  
## Création d'une activité personnalisée  
 Procédez comme suit pour créer une activité personnalisée à l'aide du concepteur d'activités :  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter une activité**.  
  
2.  Sélectionnez le modèle **Activité** ou **Activité \(avec séparation de code\)**.  
  
    1.  Utilisez le modèle **Activité** pour créer une activité comportant la définition d'activité et le code utilisateur dans le même fichier de code.  
  
    2.  Utilisez le modèle **Activité \(avec séparation de code\)** pour créer une activité comportant la définition d'activité sous forme de balisage du workflow et le code utilisateur dans un fichier de code séparé.  
  
3.  Tapez un nom d'activité ou conservez le nom par défaut, puis cliquez sur **Ajouter**.  
  
 Vous pouvez également créer un jeu d'activités personnalisées en créant un nouveau projet de type **Workflow Activity Library**.Pour plus d'informations sur ce type de projet, consultez [Procédure : créer une bibliothèque d'activités de workflow \(héritée\)](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md).  
  
## Configuration d'une activité  
 Lorsque le concepteur d'activités est actif, vous pouvez utiliser l'explorateur de propriétés pour configurer les propriétés répertoriées dans le tableau suivant.  
  
|Propriété|Commentaires|  
|---------------|------------------|  
|**Name**|Nom de l'activité.|  
|**Base Class**|Classe de base dont dérive l'activité.La classe de base par défaut est [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020).Dans la fenêtre **Propriétés**, cliquez sur les boutons de sélection de la **classe de base** \(**\[.\]**\) pour sélectionner une autre classe de base dans la [Rechercher et sélectionner un type .NET, boîte de dialogue \(héritée\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|  
|**Description**|Description de l'activité définie par l'utilisateur.|  
|**Enabled**|Affectez par défaut la valeur **True** pour activer l'exécution et la validation de l'activité.Affectez la valeur **False** pour désactiver l'exécution et la validation de l'activité.Pour plus d'informations sur l'exécution et la validation d'activités, consultez [Développement d'activités de workflow](http://go.microsoft.com/fwlink?LinkID=65024) \(page pouvant être en anglais\).|  
  
## Ajout d'activités enfants  
 Vous pouvez faire glisser des activités enfants de la boîte à outils vers l'activité que vous concevez.Vous pouvez ensuite configurer chaque activité enfant à l'aide de l'explorateur de propriétés.  
  
## Voir aussi  
 [Développement d'activités Workflow](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Création d'activités personnalisées](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Activités de workflow héritées](../workflow-designer/legacy-workflow-activities.md)   
 [Exemples d'activités personnalisées](http://go.microsoft.com/fwlink?LinkID=65022)   
 [Procédure : créer une bibliothèque d'activités de workflow \(héritée\)](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md)   
 [Utilisation du Concepteur de Workflow hérité](../workflow-designer/using-the-legacy-workflow-designer.md)
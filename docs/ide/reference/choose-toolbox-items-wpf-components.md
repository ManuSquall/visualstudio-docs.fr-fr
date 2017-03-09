---
title: "Choisir des &#233;l&#233;ments de bo&#238;te &#224; outils, Composants WPF | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.chooseitems.wpfcomponents"
helpviewer_keywords: 
  - "Composants WPF, onglet de la boîte de dialogue Choisir des éléments de boîte à outils"
  - "boîte de dialogue Choisir des éléments de boîte à outils, onglet Composants WPF"
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Choisir des &#233;l&#233;ments de bo&#238;te &#224; outils, Composants WPF
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cet onglet de la boîte de dialogue **Choisir des éléments de boîte à outils** affiche une liste des contrôles Windows Presentation Foundation \(WPF\) disponibles sur l'ordinateur local.  Pour afficher la liste, sélectionnez **Choisir des éléments de boîte à outils** dans le menu **Outils** pour afficher la boîte de dialogue **Choisir des éléments de boîte à outils**, puis sélectionnez l'onglet **Composants WPF**.  Pour trier la liste des composants, cliquez sur un en\-tête de colonne.  
  
-   Lorsque la case à cocher située à côté d'un composant est activée, l'icône de ce composant est affichée dans la **Boîte à outils**.  
  
    > [!TIP]
    >  Pour ajouter une instance d'un contrôle WPF à un document de projet ouvert en mode édition, faites glisser l'icône correspondante de la **Boîte à outils** sur la surface du mode Design.  Le balisage et le code par défaut du composant sont insérés dans votre projet, prêts à être modifiés.  Pour plus d'informations, consultez [How to: Manage the Toolbox Window](http://msdn.microsoft.com/fr-fr/a022c3fe-298c-4a59-a48f-b050da90ebc2) et [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/fr-fr/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
-   Lorsque la case à cocher située à côté d'un composant est désactivée, l'icône correspondante est supprimée de la **Boîte à outils**.  
  
    > [!NOTE]
    >  Les composants .NET Framework installés sur votre ordinateur restent disponibles, que leurs icônes soient affichées ou non dans la **Boîte à outils**.  
  
 Les colonnes de l'onglet **Composants WPF** contiennent les informations suivantes :  
  
 Nom  
 Répertorie les noms des contrôles WPF possédant des entrées dans le Registre de votre ordinateur.  
  
 Espace de noms  
 Affiche la hiérarchie de l'espace de noms [NIB: .NET Framework Class Library](http://msdn.microsoft.com/fr-fr/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) qui définit la structure du composant.  Effectuez un tri sur cette colonne pour répertorier les composants disponibles dans chaque espace de noms .NET Framework installé sur votre ordinateur.  
  
 Nom de l'assembly  
 Affiche le nom de l'assembly .NET Framework qui inclut l'espace de noms de chaque composant.  Effectuez un tri sur cette colonne pour répertorier les espaces de noms contenus dans chaque assembly .NET Framework installé sur votre ordinateur.  
  
 Répertoire  
 Affiche l'emplacement de l'assembly .NET Framework.  L'emplacement par défaut de tous les assemblys est le Global Assembly Cache.  Pour obtenir plus d'informations sur le Global Assembly Cache, consultez [Utilisation d'assemblys et du Global Assembly Cache](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md).  
  
## Liste UIElement  
 **Filter**  
 Filtre la liste de contrôles WPF en fonction de la chaîne fournie dans la zone de texte.  Les correspondances de chacune des quatre colonnes sont affichées.  
  
 **Clear**  
 Efface la chaîne de filtrage.  
  
 **Parcourir**  
 Ouvre la boîte de dialogue **Ouvrir** qui vous permet d'accéder aux assemblys contenant des contrôles WPF.  Utilisez\-la pour charger les assemblys qui ne figurent pas dans le Global Assembly Cache.  
  
 **Language**  
 Affiche la langue localisée de l'assembly qui contient le contrôle WPF sélectionné.  
  
## Limitations  
 L'ajout d'un contrôle personnalisé ou d'un <xref:System.Windows.Controls.UserControl> à la boîte à outils présente les limitations suivantes.  
  
-   Fonctionne uniquement avec les contrôles personnalisés définis à l'extérieur du projet actuel.  
  
-   Ne se met pas à jour correctement lorsque vous passez de la configuration de solution Debug à une configuration Release, ou inversement.  En effet, la référence n'est pas une référence de projet, mais est destinée à l'assembly sur le disque.  Si le contrôle fait partie de la solution actuelle, lorsque vous passez de Debug à Release, votre projet continue à référencer la version Debug du contrôle.  
  
 De plus, si les métadonnées au moment du design sont appliquées au contrôle personnalisé et que ces métadonnées spécifient que <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> a la valeur `false`, le contrôle n'apparaît pas dans la boîte à outils.  
  
 Vous pouvez référencer directement vos contrôles en XAML en mappant l'espace de noms et l'assembly de votre contrôle.  Pour plus d'informations, consultez [Comment : importer un espace de noms en XAML](http://msdn.microsoft.com/fr-fr/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).  
  
## Voir aussi  
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [boîte à outils](../../ide/reference/toolbox.md)   
 [Comment : utiliser un contrôle WPF tiers dans une application WPF](http://msdn.microsoft.com/fr-fr/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)
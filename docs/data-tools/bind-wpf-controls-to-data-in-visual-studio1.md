---
title: "Liaison de contr&#244;les WPF avec des donn&#233;es dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (WPF), afficher"
  - "liaison de données, WPF"
  - "afficher les données, WPF"
  - "WPF (WPF), données"
  - "liaison de données WPF (Visual Studio)"
  - "concepteur WPF, liaison de données"
  - "WPF, liaison de données dans Visual Studio"
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 36
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Liaison de contr&#244;les WPF avec des donn&#233;es dans Visual Studio
Vous pouvez afficher des données pour les utilisateurs de votre application en liant des données à des contrôles [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)].  Pour créer ces contrôles liés aux données, vous pouvez faire glisser les éléments depuis la fenêtre **Sources de données** vers le [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Cette rubrique décrit quelques tâches, outils et classes les plus courants que vous pouvez utiliser pour créer des applications [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] liées aux données.  
  
 Pour plus d'informations sur la création de contrôles liés aux données dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consultez [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Pour plus d'informations sur la liaison de données [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)], consultez [Vue d'ensemble de la liaison de données](../Topic/Data%20Binding%20Overview.md).  
  
## Tâches impliquées dans la liaison de contrôles WPF aux données  
 Le tableau suivant répertorie les tâches qui peuvent être accomplies en faisant glisser des éléments de la fenêtre **Sources de données** vers le [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  
  
|Tâche|Complément d'information|  
|-----------|------------------------------|  
|Créer des contrôles liés aux données.<br /><br /> Lier des contrôles existants à des données.|[Comment : lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)|  
|Créer des contrôles qui affichent les données connexes d'une relation parent\-enfant : lorsque l'utilisateur sélectionne un enregistrement de données parentes dans un contrôle, un autre contrôle affiche les données enfants connexes pour l'enregistrement sélectionné.|[Comment : afficher des données connexes dans des applications WPF](../data-tools/display-related-data-in-wpf-applications.md)|  
|Créer une *table de correspondance* qui affiche les informations provenant d'une table en fonction de la valeur d'un champ de clé étrangère d'une autre table.|[Comment : créer des tables de correspondance dans des applications WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|Lier un contrôle à une image dans une base de données.|[Comment : lier des contrôles à des images d'une base de données](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## Cibles de déplacement valides  
 Vous pouvez faire glisser des éléments dans la fenêtre **Sources de données** uniquement vers les cibles de déplacement valides dans le [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  Il existe deux genres principaux de cibles de déplacement valides : conteneurs et contrôles.  Un conteneur est un élément d'interface utilisateur qui contient généralement des contrôles.  Par exemple, une grille est un conteneur, de même qu'une fenêtre.  
  
## XAML généré et code  
 Lorsque vous faites glisser un élément de la fenêtre **Sources de données** vers le [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère le [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui définit un nouveau contrôle lié aux données \(ou lie un contrôle existant à la source de données\).  Pour certaines sources de données, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère également du code dans le fichier code\-behind qui remplit la source de données avec les données.  
  
 Le tableau suivant répertorie le code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] ainsi que le code généré par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour chaque type de source de données dans la fenêtre **Sources de données**.  
  
|Source de données|Générer le code XAML qui lie un contrôle à la source de données|Générer du code qui remplit la source de données avec les données|  
|-----------------------|---------------------------------------------------------------------|-----------------------------------------------------------------------|  
|Groupe de données|Oui|Oui|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Oui|Oui|  
|Service|Oui|Non|  
|Objet|Oui|Non|  
  
### Groupes de données  
 Lorsque vous faites glisser une table ou une colonne de la fenêtre **Sources de données** vers le concepteur, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère du code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui effectue les opérations suivantes :  
  
-   Ajoute le groupe de données \(dataset\) et un nouveau <xref:System.Windows.Data.CollectionViewSource> aux ressources du conteneur vers lequel vous avez fait glisser l'élément.  Le <xref:System.Windows.Data.CollectionViewSource> est un objet qui peut être utilisé pour naviguer et pour afficher les données dans le groupe de données.  
  
-   Crée une liaison de données pour un contrôle.  Si vous faites glisser l'élément vers un contrôle existant dans le concepteur, le code XAML lie le contrôle à l'élément.  Si vous faites glisser l'élément vers un conteneur, le code XAML crée le contrôle sélectionné pour l'élément déplacé et lie le contrôle à l'élément.  Le contrôle est créé dans une nouvelle <xref:System.Windows.Controls.Grid>.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] apporte également les modifications suivantes au fichier code\-behind :  
  
-   Crée un gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded> pour l'élément [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] qui contient le contrôle.  Le gestionnaire d'événements remplit la table des données, extrait le <xref:System.Windows.Data.CollectionViewSource> des ressources du conteneur, puis active le premier élément de données comme élément de données actuel.  Si un gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded> existe déjà, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ajoute ce code au gestionnaire existant.  
  
### Entity Data Models  
 Lorsque vous faites glisser une entité ou une propriété d'entité de la fenêtre **Sources de données**, vers le concepteur, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère du code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui effectue les opérations suivantes :  
  
-   Ajoute un nouveau <xref:System.Windows.Data.CollectionViewSource> aux ressources du conteneur vers lequel vous avez fait glisser l'élément.  Le <xref:System.Windows.Data.CollectionViewSource> est un objet qui peut être utilisé pour naviguer et pour afficher les données dans l'entité.  
  
-   Crée une liaison de données pour un contrôle.  Si vous faites glisser l'élément vers un contrôle existant dans le concepteur, le code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] lie le contrôle à l'élément.  Si vous faites glisser l'élément vers un conteneur, le code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crée le contrôle sélectionné pour l'élément déplacé et lie le contrôle à l'élément.  Le contrôle est créé dans une nouvelle <xref:System.Windows.Controls.Grid>.  
  
 Visual Studio apporte également les modifications suivantes au fichier code\-behind :  
  
-   Ajoute une nouvelle méthode qui retourne une requête pour l'entité que vous avez fait glisser vers le concepteur \(ou l'entité qui contient la propriété que vous avez fait glisser vers le concepteur\).  La nouvelle méthode porte le nom Get*NomEntité*Query, où *NomEntité* est le nom de l'entité.  
  
-   Crée un gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded> pour l'élément [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] qui contient le contrôle.  Le gestionnaire d'événements appelle la méthode Get*NomEntité*Query pour remplir l'entité avec des données, extrait le <xref:System.Windows.Data.CollectionViewSource> des ressources du conteneur, puis active le premier élément de données comme élément actuel.  Si un gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded> existe déjà, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ajoute ce code au gestionnaire existant.  
  
### Services  
 Lorsque vous faites glisser un objet de service ou une propriété de la fenêtre **Sources de données** vers le concepteur, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère du code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui crée un contrôle lié aux données \(ou lie un contrôle existant à l'objet ou à la propriété\).  Toutefois, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne génère pas de code qui remplit l'objet de service proxy avec les données.  Vous devez écrire ce code vous\-même.  Pour obtenir un exemple qui montre comment procéder, consultez [Procédure pas à pas : liaisons de contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
 Visual Studio génère du code XAML qui effectue les opérations suivantes :  
  
-   Ajoute un nouveau <xref:System.Windows.Data.CollectionViewSource> aux ressources du conteneur vers lequel vous avez fait glisser l'élément.  Le <xref:System.Windows.Data.CollectionViewSource> est un objet qui peut être utilisé pour naviguer et pour afficher les données dans l'objet retourné par le service.  
  
-   Crée une liaison de données pour un contrôle.  Si vous faites glisser l'élément vers un contrôle existant dans le concepteur, le code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] lie le contrôle à l'élément.  Si vous faites glisser l'élément vers un conteneur, le code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crée le contrôle sélectionné pour l'élément déplacé et lie le contrôle à l'élément.  Le contrôle est créé dans une nouvelle <xref:System.Windows.Controls.Grid>.  
  
### Objets  
 Lorsque vous faites glisser un objet ou une propriété de la fenêtre **Sources de données** vers le concepteur, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère du code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui crée un contrôle lié aux données \(ou lie un contrôle existant à l'objet ou à la propriété\).  Toutefois, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne génère pas de code pour remplir l'objet avec les données.  Vous devez écrire ce code vous\-même.  
  
> [!NOTE]
>  Les classes personnalisées doivent être publiques et posséder un constructeur sans paramètre par défaut.  Il ne peut pas s'agir de classes imbriquées qui ont un "point" dans leur syntaxe.  Pour plus d'informations, consultez [XAML et classes personnalisées pour WPF](../Topic/XAML%20and%20Custom%20Classes%20for%20WPF.md).  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère du code [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] qui effectue les opérations suivantes :  
  
-   Ajoute un nouveau <xref:System.Windows.Data.CollectionViewSource> aux ressources du conteneur vers lequel vous avez fait glisser l'élément.  Le <xref:System.Windows.Data.CollectionViewSource> est un objet qui peut être utilisé pour naviguer et pour afficher les données dans l'objet.  
  
-   Crée une liaison de données pour un contrôle.  Si vous faites glisser l'élément vers un contrôle existant dans le concepteur, le code XAML lie le contrôle à l'élément.  Si vous faites glisser l'élément vers un conteneur, le code XAML crée le contrôle sélectionné pour l'élément déplacé et lie le contrôle à l'élément.  Le contrôle est créé dans une nouvelle <xref:System.Windows.Controls.Grid>.  
  
## Voir aussi  
 [Comment : lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Comment : créer des tables de correspondance dans des applications WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Comment : afficher des données connexes dans des applications WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Liaison de contrôles WPF avec un modèle Entity Data Model](http://msdn.microsoft.com/data/jj574514.aspx)   
 [Procédure pas à pas : liaison de contrôles WPF avec un groupe de données](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Procédure pas à pas : liaisons de contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Procédure pas à pas : affichage de données connexes dans une application WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)   
 [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)
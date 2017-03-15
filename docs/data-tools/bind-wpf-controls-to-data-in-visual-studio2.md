---
title: "Comment&#160;: lier des contr&#244;les WPF &#224; des donn&#233;es dans Visual Studio | Microsoft Docs"
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
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 26
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: lier des contr&#244;les WPF &#224; des donn&#233;es dans Visual Studio
Vous pouvez créer des contrôles [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] liés aux données à l'aide de la fenêtre **Sources de données**.  Pour commencer, ajoutez une source de données à la fenêtre **Sources de données**.  Ensuite, faites glisser des éléments depuis la fenêtre **Sources de données** vers le **Concepteur WPF**.  
  
##  <a name="adding"></a> Ajout d'une source de données à la fenêtre Sources de données  
 Avant de pouvoir créer des contrôles liés aux données, vous devez d'abord ajouter une source de données à la fenêtre **Sources de données**.  
  
#### Pour ajouter une source de données à la fenêtre Sources de données  
  
1.  Dans le menu **Affichage**, choisissez **Autres fenêtres**, puis cliquez sur **Sources de données**.  
  
2.  Cliquez sur **Ajouter une nouvelle source de données** et suivez les étapes de l'**Assistant Configuration de source de données**.  
  
3.  Effectuez l'une des tâches suivantes pour créer des contrôles liés aux données :  
  
    -   [Création d'un contrôle lié à un seul champ de données](#simple).  
  
    -   [Création d'un contrôle lié à plusieurs champs de données](#complex).  
  
    -   [Création d'un ensemble de contrôles liés à plusieurs champs de données](#details).  
  
    -   [Liaison de données à des contrôles existants dans le concepteur](#existing).  
  
##  <a name="simple"></a> Création d'un contrôle lié à un seul champ de données  
 Après avoir ajouté une source de données à la fenêtre **Sources de données**, vous pouvez créer un contrôle lié aux données affichant un seul champ de données, tel que <xref:System.Windows.Controls.ComboBox> ou <xref:System.Windows.Controls.TextBox>.  
  
#### Pour créer un contrôle lié à un seul champ de données  
  
1.  Dans la fenêtre **Sources de données**, développez un élément représentant une table ou un objet.  Recherchez l'élément enfant représentant la colonne ou la propriété que vous voulez lier.  Pour obtenir un exemple visuel, consultez [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  
  
2.  Sélectionnez éventuellement le contrôle à créer.  Chaque élément de la fenêtre **Sources de données** possède un contrôle par défaut créé quand vous faites glisser l'élément dans le concepteur.  Le contrôle par défaut dépend du type de données sous\-jacent de l'élément.  
  
     Pour choisir un autre contrôle, cliquez sur la flèche déroulante à côté de l'élément et sélectionnez un contrôle.  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Faites glisser l'élément vers un conteneur valide du concepteur, comme <xref:System.Windows.Controls.Grid>.  Pour plus d'informations sur les conteneurs valides, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée le contrôle lié aux données et un <xref:System.Windows.Controls.Label> avec un titre approprié dans le conteneur.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère également [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] et le code pour lier le contrôle aux données.  Pour plus d'informations, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="complex"></a> Création d'un contrôle lié à plusieurs champs de données  
 Après avoir ajouté une source de données à la fenêtre **Sources de données**, vous pouvez créer un contrôle lié aux données affichant plusieurs champs de données, tel que <xref:System.Windows.Controls.DataGrid> ou <xref:System.Windows.Controls.ListView>.  
  
#### Pour créer un contrôle lié à plusieurs champs de données  
  
1.  Dans la fenêtre **Sources de données**, sélectionnez un élément qui représente une table ou un objet.  Pour obtenir un exemple visuel, consultez [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  
  
2.  Sélectionnez éventuellement le contrôle à créer.  Par défaut, chaque élément de la fenêtre **Sources de données** représentant une table de données ou un objet est défini de sorte à créer un <xref:System.Windows.Controls.DataGrid> \(si votre projet cible .NET Framework 4\) ou <xref:System.Windows.Controls.ListView> \(pour les versions antérieures de .NET Framework\).  
  
     Pour choisir un autre contrôle, cliquez sur la flèche déroulante à côté de l'élément et sélectionnez un contrôle.  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Si vous ne voulez pas afficher une colonne ou propriété particulière, développez l'élément pour afficher ses enfants.  Cliquez sur la flèche déroulante à côté de la colonne ou propriété à masquer, puis cliquez sur **Aucun**.  
  
3.  Faites glisser l'élément vers un conteneur valide du concepteur, comme <xref:System.Windows.Controls.Grid>.  Pour plus d'informations sur les conteneurs valides, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée le contrôle lié aux données dans le conteneur. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère également [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] et le code pour lier le contrôle aux données.  Pour plus d'informations, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="details"></a> Création d'un ensemble de contrôles liés à plusieurs champs de données  
 Après avoir ajouté une source de données à la fenêtre **Sources de données**, vous pouvez lier une table de données ou un objet à un ensemble de contrôles.  Un autre contrôle est créé pour chaque colonne ou propriété dans la table ou l'objet.  
  
#### Pour créer un ensemble de contrôles liés à plusieurs champs de données  
  
1.  Dans la fenêtre **Sources de données**, sélectionnez un élément qui représente une table ou un objet.  Pour obtenir un exemple visuel, consultez [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  
  
2.  Cliquez sur la flèche déroulante à côté de l'élément et sélectionnez **Détails**.  
  
    > [!NOTE]
    >  Si vous ne voulez pas afficher une colonne ou propriété particulière, développez l'élément pour afficher ses enfants.  Cliquez sur la flèche déroulante à côté de la colonne ou propriété à masquer, puis cliquez sur **Aucun**.  
  
3.  Faites glisser l'élément vers un conteneur valide du concepteur, comme <xref:System.Windows.Controls.Grid>.  Pour plus d'informations sur les conteneurs valides, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée les contrôles liés aux données dans le conteneur.  Chaque contrôle est lié à une colonne ou propriété différente, et chaque contrôle est accompagné d'un contrôle <xref:System.Windows.Controls.Label> avec un titre approprié. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère aussi [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] et le code pour lier les contrôles aux données.  Pour plus d'informations, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="existing"></a> Liaison de données à des contrôles existants dans le concepteur  
 Après avoir ajouté une source de données à la fenêtre **Sources de données**, vous pouvez ajouter une liaison de données à un contrôle existant dans le concepteur.  
  
#### Pour lier des données à un contrôle existant dans le concepteur  
  
1.  Dans la fenêtre **Sources de données**, utilisez l'une des procédures suivantes :  
  
    -   Pour ajouter une liaison de données à un contrôle existant affichant plusieurs champs de données, tel que <xref:System.Windows.Controls.DataGrid> ou <xref:System.Windows.Controls.ListView>, sélectionnez l'élément représentant la table ou l'objet que vous voulez lier au contrôle.  
  
    -   Pour ajouter une liaison de données à un contrôle existant affichant un seul champ de données, tel que <xref:System.Windows.Controls.ComboBox> ou <xref:System.Windows.Controls.TextBox>, développez l'élément représentant la table ou l'objet qui contient les données, puis sélectionnez l'élément représentant les données à lier au contrôle.  
  
2.  Faites glisser l'élément sélectionné depuis la fenêtre **Sources de données** vers un contrôle existant dans le concepteur.  Le contrôle doit être une cible de déplacement valide.  Pour plus d'informations, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] et le code pour lier le contrôle aux données.  Pour plus d'informations, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
    > [!NOTE]
    >  Si le contrôle est déjà lié aux données, la liaison de données pour le contrôle est redéfinie sur l'élément qui a été le plus récemment déplacé vers le contrôle.  
  
## Voir aussi  
 [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Comment : créer des tables de correspondance dans des applications WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Comment : afficher des données connexes dans des applications WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Procédure pas à pas : liaison de contrôles WPF avec un groupe de données](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Procédure pas à pas : liaisons de contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Procédure pas à pas : affichage de données connexes dans une application WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
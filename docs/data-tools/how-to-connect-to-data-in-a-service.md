---
title: "Comment&#160;: se connecter &#224; des donn&#233;es dans un service | Microsoft Docs"
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
  - "données (Visual Studio), se connecter à des services Web"
  - "données (Visual Studio), lire à partir de services Web"
  - "sources de données, créer à partir de services Web"
  - "lire des données, à partir de services Web"
  - "services Web, comme sources de données"
  - "services Web, connecter"
  - "services Web, lire des données"
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: se connecter &#224; des donn&#233;es dans un service
Vous connectez votre application aux données retournées par un service en exécutant l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png) et en sélectionnant **Service** sur la page **Choisir un type de source de données**.  
  
 Au terme de l'Assistant, une référence au service est ajoutée à votre projet et est immédiatement disponible dans la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  
  
> [!NOTE]
>  Les éléments qui s'affichent dans la fenêtre **Sources de données** dépendent des informations retournées par le service.  Il se peut que certains services ne fournissent pas suffisamment d'informations pour permettre à l'**Assistant Configuration de source de données** de créer des objets pouvant être liés.  Par exemple, si le service retourne un dataset non typé, aucun élément ne s'affiche dans la fenêtre **Sources de données** une fois l'Assistant terminé.  Cela est dû au fait que les groupes de données non typés ne fournissent pas de schéma. L'Assistant ne possède donc pas suffisamment d'informations pour créer la source de données.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Pour connecter votre application à un service  
  
1.  Dans le menu **Données**, cliquez sur **Ajouter une nouvelle source de données**.  
  
2.  Sélectionnez **Service** sur la page **Choisir un type de source de données**, puis cliquez sur **Suivant**.  
  
3.  Entrez l'adresse du service que vous souhaitez utiliser ou cliquez sur **Découvrir** pour rechercher les services dans la solution actuelle, puis cliquez sur **Aller à**.  
  
4.  Vous pouvez éventuellement taper un nouvel **Espace de noms** à la place de la valeur par défaut.  
  
    > [!NOTE]
    >  Cliquez sur **Avancé** pour ouvrir la [Configurer la référence de service, boîte de dialogue](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Cliquez sur **OK** pour ajouter une référence de service à votre projet.  
  
6.  Cliquez sur **Terminer**.  
  
     La source de données est ajoutée à la fenêtre **Sources de données**.  
  
## Étapes suivantes  
  
#### Pour ajouter des fonctionnalités à votre application  
  
-   Sélectionnez un élément dans la fenêtre **Sources de données** et faites\-le glisser jusqu'à un formulaire pour créer des contrôles liés.  Pour plus d'informations, consultez [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## Voir aussi  
 [Procédure pas à pas : liaisons de contrôles WPF à un service de données WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Procédure pas à pas : liaisons de contrôles Silverlight à un service de données WCF](../Topic/Walkthrough:%20Binding%20Silverlight%20Controls%20to%20a%20WCF%20Data%20Service.md)   
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
---
title: "Prise en charge des formulaires dans les flux de travail"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, workflows"
  - "workflows (développement SharePoint dans Visual Studio)"
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Prise en charge des formulaires dans les flux de travail
  Quatre types de formulaires peuvent être utilisés dans un flux de travail : association, initiation, tâche et modification.  Ces types de formulaires peuvent être basés sur un formulaire ASPX ou un formulaire InfoPath.  Le niveau de support que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fournit pour un formulaire spécifique dépend de plusieurs facteurs, décrits dans les tableaux suivants.  Pour plus d'informations sur les types de format de flux de travail, consultez [Présentation de Formats de Flux de Travail](http://go.microsoft.com/fwlink/?LinkId=185228) sur le site Web de MSDN.  
  
## Refactorisation XML  
 Lorsque vous ajoutez un formulaire d'association ou d'initiation ASPX à un élément de projet de flux de travail [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] refactorise automatiquement le code XML dans le fichier Elements.xml du flux de travail pour conserver l'attribut qui fait référence au formulaire d'association ou d'initiation synchronisé à chaque fois que le nom de formulaire ou chemin de déploiement est mis à jour ou que le formulaire est supprimé.  Toutefois, lorsque vous utilisez d'autres types de formulaires dans un flux de travail, tel qu'un formulaire de tâche ou de modification, le fichier Elements.xml n'est pas refactorisé.  
  
## Prise en charge des formulaires dans les nouveaux flux de travail Visual Studio  
 Le tableau suivant répertorie la prise en charge [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] de différents types de formulaires basés sur formulaires ASPX ou InfoPath dans les flux de travail créés dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Type de formulaire|Flux de travail créé dans Visual Studio avec un formulaire ASPX|Flux de travail créé dans Visual Studio avec un formulaire InfoPath|  
|------------------------|---------------------------------------------------------------------|-------------------------------------------------------------------------|  
|Association|-   Un formulaire d'association ASPX peut être ajouté au flux de travail à l'aide du modèle d'élément **Formulaire d'association du flux de travail**.<br />-   Le fichier Elements.xml du flux de travail est refactorisé lorsque le formulaire est ajouté, renommé ou supprimé, ou lorsque son chemin de déploiement change.<br />-   Pour plus d'informations, consultez [Procédure pas à pas : création d'un flux de travail avec des formulaires d'association et d'initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-   Il n'existe aucun modèle de formulaire d'association InfoPath dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Il n'existe aucune intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-   Le fichier Elements.xml du flux de travail n'est pas refactorisé.|  
|Initiation|-   Un formulaire d'initiation ASPX peut être ajouté au flux de travail à l'aide du modèle d'élément **Formulaire d'initiation du flux de travail**.<br />-   Le fichier Elements.xml du flux de travail est refactorisé lorsque le formulaire est ajouté, renommé ou supprimé, ou lorsque son chemin de déploiement change.<br />-   Pour plus d'informations, consultez [Procédure pas à pas : création d'un flux de travail avec des formulaires d'association et d'initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-   Il n'existe aucun modèle de formulaire d'association InfoPath dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Il n'existe aucune intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-   Le fichier Elements.xml du flux de travail n'est pas refactorisé.|  
|Tâche|-   Aucun modèle de formulaire de tâche ASPX n'est disponible dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Vous devez créer une page d'application et lui ajouter le code.<br />-   Le fichier Elements.xml du flux de travail n'est pas refactorisé.<br />-   Pour plus d'informations, consultez [Formulaires de tâches de flux de travail \(base SharePoint\)](http://go.microsoft.com/fwlink/?LinkId=187674)|-   Il n'existe aucun modèle de formulaire de tâche InfoPath dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Il n'existe aucune intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-   Le fichier Elements.xml du flux de travail n'est pas refactorisé.|  
|Modification|-   Aucun modèle de formulaire de modification ASPX n'est disponible dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Pour ajouter un formulaire de modification, vous devez créer une page d'application et lui ajouter le code.<br />-   Le fichier Elements.xml du flux de travail n'est pas refactorisé.  Vous devez le modifier manuellement si nécessaire.<br />-   Pour plus d'informations, consultez [Formes de modification de flux de travail \(base SharePoint\)](http://go.microsoft.com/fwlink/?LinkId=187675)|-   Il n'existe aucun modèle de formulaire de modification InfoPath dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Il n'existe aucune intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-   Le fichier Elements.xml du flux de travail n'est pas refactorisé.|  
  
## Prise en charge des formulaires dans les flux de travail réutilisables SharePoint importés  
 Le tableau suivant répertorie la prise en charge [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour les différents types de formulaires basés sur formulaires ASPX ou InfoPath dans les flux de travail réutilisables SharePoint importés dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Type de formulaire|Flux de travail réutilisable pour lequel un formulaire ASPX est importé à partir de SharePoint Designer|Flux de travail réutilisable pour lequel un formulaire InfoPath est importé à partir de SharePoint Designer|  
|------------------------|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|  
|Association|-   Le formulaire est référencé dans le fichier Elements.xml du flux de travail.<br />-   Le fichier Elements.xml du flux de travail est refactorisé lorsque le formulaire est renommé ou supprimé, ou lorsque son chemin de déploiement change.|-   Le formulaire est importé, mais non référencé dans le fichier Elements.xml du flux de travail.<br />-   Le fichier Elements.xml du flux de travail n'est pas refactorisé.|  
|Initiation|-   Le formulaire est référencé par le flux de travail dans le fichier Elements.xml du flux de travail.<br />-   Le fichier Elements.xml du flux de travail est refactorisé lorsque le formulaire est renommé ou supprimé, ou lorsque son chemin de déploiement change.|-   Le formulaire est importé, mais non référencé dans le fichier Elements.xml du flux de travail.<br />-   Le fichier Elements.xml du flux de travail n'est pas refactorisé. **Note:**  Les règles et propriétés doivent être ajoutées et modifiées pour que ce scénario fonctionne.|  
|Tâche|-   Le formulaire est référencé dans le fichier Elements.xml du flux de travail.<br />-   Le fichier Elements.xml du flux de travail n'est pas refactorisé.|-   Le formulaire est importé, mais non référencé dans le fichier Elements.xml du flux de travail.<br />-   Le fichier Elements.xml du flux de travail n'est pas refactorisé. **Note:**  Les règles et propriétés doivent être ajoutées et modifiées pour que ce scénario fonctionne.|  
|Modification|Non applicable.  Les formulaires de modification ASPX ne peuvent pas être créés dans SharePoint Designer.|Non applicable.  Les formulaires de modification InfoPath ne peuvent pas être créés dans SharePoint Designer, à l'exception du flux de travail SharePoint Server intégré, qui n'est pas inclus dans le fichier .wsp lorsque le flux de travail est exporté.|  
  
## Voir aussi  
 [Procédure pas à pas : création d'un flux de travail avec des formulaires d'association et d'initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Création de solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importation d'éléments d'un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  
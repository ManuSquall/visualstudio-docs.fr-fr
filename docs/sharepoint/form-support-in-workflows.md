---
title: "Écran de prise en charge dans les Workflows | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2544bbe60ea014ee873342f06ce285c809b42eb6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="form-support-in-workflows"></a>Prise en charge des formulaires dans les flux de travail
  Quatre types de formulaires peuvent être utilisés dans un flux de travail : association, initiation, tâche et la modification. Ces types de formulaire peuvent être basés sur un formulaire ASPX ou un formulaire InfoPath. Le niveau de prise en charge que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fournit pour un formulaire particulier dépend de plusieurs facteurs, qui sont décrites dans les tableaux suivants. Pour plus d’informations sur les types de formulaire de flux de travail, consultez [vue d’ensemble des formulaires de flux de travail](http://go.microsoft.com/fwlink/?LinkId=185228) sur le site Web MSDN.  
  
## <a name="xml-refactoring"></a>Refactorisation de XML  
 Lorsque vous ajoutez un formulaire d’association ou d’initiation ASPX à un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] élément de projet de flux de travail, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automatiquement refactorise le code XML dans le fichier Elements.xml du flux de travail pour conserver l’attribut qui fait référence au formulaire d’association ou l’émission de la synchronisation chaque fois que la forme nom ou chemin de déploiement est mis à jour ou le formulaire est supprimé. Toutefois, lorsque vous utilisez d’autres types de formulaires dans un flux de travail, tel qu’un formulaire de tâche ou de modification, le fichier Elements.xml n’est pas refactorisé.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Prise en charge de formulaire dans les nouveaux flux de travail de Visual Studio  
 Le tableau suivant répertorie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] prise en charge de différents types de formulaires sur les formulaires ASPX ou InfoPath dans les workflows créés dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Type de formulaire|Flux de travail créé dans Visual Studio avec un formulaire ASPX|Flux de travail créé dans Visual Studio à l’aide d’un formulaire InfoPath|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Association|-Un formulaire d’association ASPX peut être ajouté au flux de travail à l’aide de la **formulaire d’Association de flux de travail** modèle d’élément.<br />-Le fichier Elements.xml du flux de travail est refactorisé lorsque le formulaire est ajouté, renommé ou supprimé, ou lorsque son chemin de déploiement change.<br />-Pour plus d’informations, consultez [procédure pas à pas : création d’un flux de travail avec l’Association et des formulaires d’Initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Il n’existe aucun modèle de formulaire d’association dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Il n’existe pas d’intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-Le fichier Elements.xml du flux de travail n’est pas refactorisé.|  
|Émission|-Un formulaire d’initiation ASPX peut être ajouté au flux de travail à l’aide de la **formulaire d’Initiation du flux de travail** modèle d’élément.<br />-Le fichier Elements.xml du flux de travail est refactorisé lorsque le formulaire est ajouté, renommé ou supprimé, ou lorsque son chemin de déploiement change.<br />-Pour plus d’informations, consultez [procédure pas à pas : création d’un flux de travail avec l’Association et des formulaires d’Initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Il n’existe aucun modèle de formulaire d’association dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Il n’existe pas d’intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-Le fichier Elements.xml du flux de travail n’est pas refactorisé.|  
|Tâche|-Aucun modèle de formulaire de tâche ASPX n’est disponible dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Vous devez créer une page d’application et ajouter du code.<br />-Le fichier Elements.xml du flux de travail n’est pas refactorisé.<br />-Pour plus d’informations, consultez [formulaires de tâche de flux de travail (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-Il n’existe aucun modèle de formulaire de tâche InfoPath dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Il n’existe pas d’intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-Le fichier Elements.xml du flux de travail n’est pas refactorisé.|  
|Modification|-Aucun modèle de formulaire de modification ASPX n’est disponible dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour ajouter un formulaire de modification, vous devez créer une page d’application et ajouter du code.<br />-Le fichier Elements.xml du flux de travail n’est pas refactorisé. Vous devez modifier manuellement comme il convient.<br />-Pour plus d’informations, consultez [formulaires de Modification de flux de travail (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-Il n’existe aucun modèle de formulaire InfoPath modification dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Il n’existe pas d’intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-Le fichier Elements.xml du flux de travail n’est pas refactorisé.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Prise en charge de la forme de flux de travail réutilisables SharePoint importés  
 Le tableau suivant répertorie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] prise en charge de différents types de formulaires sur des formulaires ASPX ou InfoPath dans les flux de travail réutilisables de SharePoint qui sont importés dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Type de formulaire|Flux de travail réutilisable qui comporte un formulaire ASPX importé à partir de SharePoint Designer|Flux de travail réutilisable qui a un formulaire InfoPath est importé à partir de SharePoint Designer|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Association|-Le formulaire est référencé dans le fichier Elements.xml du flux de travail.<br />-Le fichier Elements.xml du flux de travail est refactorisé lorsque le formulaire est renommé ou supprimé, ou lorsque son chemin de déploiement change.|-Le formulaire est importé, mais non référencé dans le fichier Elements.xml du flux de travail.<br />-Le fichier Elements.xml du flux de travail n’est pas refactorisé.|  
|Émission|-Le formulaire est référencé par le flux de travail dans le fichier Elements.xml du flux de travail.<br />-Le fichier Elements.xml du flux de travail est refactorisé lorsque le formulaire est renommé ou supprimé, ou lorsque son chemin de déploiement change.|-Le formulaire est importé, mais non référencé dans le fichier Elements.xml du flux de travail.<br />-Le fichier Elements.xml du flux de travail n’est pas refactorisé. **Remarque :** règles et des propriétés doivent être ajoutées et modifiées pour ce scénario fonctionne.|  
|Tâche|-Le formulaire est référencé dans le fichier Elements.xml du flux de travail.<br />-Le fichier Elements.xml du flux de travail n’est pas refactorisé.|-Le formulaire est importé, mais non référencé dans le fichier Elements.xml du flux de travail.<br />-Le fichier Elements.xml du flux de travail n’est pas refactorisé. **Remarque :** règles et des propriétés doivent être ajoutées et modifiées pour ce scénario fonctionne.|  
|Modification|Non applicable. Formulaires de modification ASPX ne peut pas être créés dans SharePoint Designer.|Non applicable. Impossible de créer des formulaires InfoPath modification dans SharePoint Designer, sauf pour le flux de travail SharePoint Server intégré, qui n’est pas inclus dans le fichier .wsp lorsque le flux de travail est exporté.|  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’un flux de travail avec l’Association et des formulaires d’Initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Création de Solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importation d’éléments d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  
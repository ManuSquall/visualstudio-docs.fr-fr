---
title: Prise en charge des formulaires dans les flux de travail | Microsoft Docs
description: 'En savoir plus sur la prise en charge des formulaires dans les flux de travail SharePoint. Quatre types de formulaires peuvent être utilisés dans un flux de travail : Association, initiation, tâche et modification.'
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52939fe00dcbca1cfd633c81d4b0a00ea6b517b9
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915503"
---
# <a name="form-support-in-workflows"></a>Prise en charge des formulaires dans les workflows
  Quatre types de formulaires peuvent être utilisés dans un flux de travail : Association, initiation, tâche et modification. Ces types de formulaires peuvent être basés sur un formulaire ASPX ou un formulaire InfoPath. Le niveau de prise en charge [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fourni pour un formulaire particulier dépend de plusieurs facteurs, qui sont décrits dans les tableaux suivants. Pour plus d’informations sur les types de formulaires de workflow, consultez [vue d’ensemble des formulaires de flux de travail](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>Refactorisation XML
 Quand vous ajoutez un formulaire d’association ou d’initiation ASPX à un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] élément de projet de workflow, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] refactorise automatiquement le XML dans le fichier de *Elements.xml* du workflow pour que l’attribut qui fait référence au formulaire d’association ou d’initiation soit synchronisé à chaque mise à jour du nom du formulaire ou du chemin d’accès, ou lorsque le formulaire est supprimé. Toutefois, lorsque vous utilisez d’autres types de formulaires dans un flux de travail, tels qu’une tâche ou un formulaire de modification, le fichier *Elements.xml* n’est pas refactorisé.

## <a name="form-support-in-new-visual-studio-workflows"></a>Prise en charge des formulaires dans les nouveaux flux de travail Visual Studio
 Le tableau suivant répertorie la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] prise en charge de différents types de formulaire sur les formulaires aspx ou InfoPath dans les workflows créés dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Type de formulaire|Flux de travail créé dans Visual Studio avec un formulaire ASPX|Flux de travail créé dans Visual Studio à l’aide d’un formulaire InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Association|-Un formulaire d’association ASPX peut être ajouté au flux de travail à l’aide du modèle d’élément de **formulaire d’association de flux de travail** .<br />-Le fichier *Elements.xml* du flux de travail est refactorisé lorsque le formulaire est ajouté, renommé ou supprimé, ou lorsque son chemin d’accès de déploiement change.<br />-Pour plus d’informations, consultez [procédure pas à pas : création d’un flux de travail avec des formulaires d’association et d’initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Il n’existe aucun modèle de formulaire d’association InfoPath dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Il n’y a pas d’intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-Le fichier *Elements.xml* du flux de travail n’est pas refactorisé.|
|Initiation|-Un formulaire d’initiation ASPX peut être ajouté au flux de travail à l’aide du modèle d’élément de **formulaire d’initiation de flux de travail** .<br />-Le fichier *Elements.xml* du flux de travail est refactorisé lorsque le formulaire est ajouté, renommé ou supprimé, ou lorsque son chemin d’accès de déploiement change.<br />-Pour plus d’informations, consultez [procédure pas à pas : création d’un flux de travail avec des formulaires d’association et d’initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Il n’existe aucun modèle de formulaire d’association InfoPath dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Il n’y a pas d’intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-Le fichier *Elements.xml* du flux de travail n’est pas refactorisé.|
|Tâche|-Aucun modèle de formulaire de tâche ASPX n’est disponible dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Vous devez créer une page d’application et y ajouter du code.<br />-Le fichier *Elements.xml* du flux de travail n’est pas refactorisé.<br />-Pour plus d’informations, consultez [formulaires de tâches de flux de travail (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14)) .|-Il n’existe aucun modèle de formulaire de tâche InfoPath dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Il n’y a pas d’intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-Le fichier *Elements.xml* du flux de travail n’est pas refactorisé.|
|Modification|-Aucun modèle de formulaire de modification ASPX n’est disponible dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Pour ajouter un formulaire de modification, vous devez créer une page d’application et y ajouter du code.<br />-Le fichier *Elements.xml* du flux de travail n’est pas refactorisé. Vous devez le modifier manuellement, le cas échéant.<br />-Pour plus d’informations, consultez [formulaires de modification de flux de travail (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14)) .|-Il n’existe aucun modèle de formulaire de modification InfoPath dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-Il n’y a pas d’intégration entre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et InfoPath Designer.<br />-Le fichier *Elements.xml* du flux de travail n’est pas refactorisé.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Prise en charge des formulaires dans les flux de travail réutilisables SharePoint importés
 Le tableau suivant répertorie la [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] prise en charge de différents types de formulaire sur les formulaires aspx ou InfoPath dans les flux de travail réutilisables SharePoint importés dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Type de formulaire|Flux de travail réutilisable avec un formulaire ASPX importé à partir de SharePoint Designer|Flux de travail réutilisable avec un formulaire InfoPath importé à partir de SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Association|-Le formulaire est référencé dans le fichier *Elements.xml* du flux de travail.<br />-Le fichier *Elements.xml* du flux de travail est refactorisé lorsque le formulaire est renommé ou supprimé, ou lorsque son chemin d’accès de déploiement change.|-Le formulaire est importé, mais n’est pas référencé dans le *Elements.xml* du flux de travail.<br />-Le fichier *Elements.xml* du flux de travail n’est pas refactorisé.|
|Initiation|-Le formulaire est référencé par le flux de travail dans le fichier *Elements.xml* du flux de travail.<br />-Le fichier *Elements.xml* du flux de travail est refactorisé lorsque le formulaire est renommé ou supprimé, ou lorsque son chemin d’accès de déploiement change.|-Le formulaire est importé, mais n’est pas référencé dans le *Elements.xml* du flux de travail.<br />-Le fichier *Elements.xml* du flux de travail n’est pas refactorisé. **Remarque :**  Les règles et les propriétés doivent être ajoutées et modifiées pour que ce scénario fonctionne.|
|Tâche|-Le formulaire est référencé dans le fichier *Elements.xml* du flux de travail.<br />-Le fichier *Elements.xml* du flux de travail n’est pas refactorisé.|-Le formulaire est importé, mais n’est pas référencé dans le *Elements.xml* du flux de travail.<br />-Le fichier *Elements.xml* du flux de travail n’est pas refactorisé. **Remarque :**  Les règles et les propriétés doivent être ajoutées et modifiées pour que ce scénario fonctionne.|
|Modification|Non applicable. Impossible de créer des formulaires de modification ASPX dans SharePoint Designer.|Non applicable. Les formulaires de modification InfoPath ne peuvent pas être créés dans SharePoint Designer, à l’exception du flux de travail SharePoint Server intégré, qui n’est pas inclus dans le fichier. wsp lorsque le flux de travail est exporté.|

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : créer un flux de travail avec des formulaires d’association et d’initiation](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Créer des solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Importer des éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)

---
title: "Personnalisation des fonctionnalit&#233;s de l&#39;interface utilisateur &#224; l&#39;aide d&#39;interfaces d&#39;extensibilit&#233; | Microsoft Docs"
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
  - "ICustomTaskPaneConsumer (interface)"
  - "IRibbonExtensibility (interface)"
  - "personnalisation de l'interface utilisateur (développement Office dans Visual Studio)"
  - "interfaces utilisateur (développement Office dans Visual Studio), personnalisation"
  - "compléments d’application (développement Office dans Visual Studio), interfaces d’extensibilité"
  - "personnaliser les fonctionnalités de l'interface utilisateur (développement Office dans Visual Studio)"
  - "FormRegionStartup (interface)"
  - "compléments (développement Office dans Visual Studio), interfaces d’extensibilité"
  - "interfaces d'extensibilité (développement Office dans Visual Studio)"
ms.assetid: 3f3f7908-9404-4eda-8899-4d18c75e3b4a
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Personnalisation des fonctionnalit&#233;s de l&#39;interface utilisateur &#224; l&#39;aide d&#39;interfaces d&#39;extensibilit&#233;
  Les Outils de développement Office dans Visual Studio fournissent des classes et des concepteurs qui gèrent de nombreux détails d’implémentation quand vous les utilisez pour créer des volets de tâches personnalisés, des personnalisations de ruban et des zones de formulaire Outlook dans un complément VSTO. Toutefois, vous pouvez également implémenter vous\-même l'*interface d'extensibilité* pour chaque fonctionnalité si vous avez des spécifications spéciales.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## Vue d'ensemble des interfaces d'extensibilité  
 Microsoft Office définit un ensemble d’interfaces d’extensibilité que les compléments VSTO COM peuvent implémenter pour personnaliser certaines fonctionnalités, comme le ruban. Ces interfaces fournissent un contrôle total sur les fonctionnalités auxquelles elles donnent accès. Toutefois, l'implémentation de ces interfaces requiert une certaine connaissance de l'interopérabilité COM dans le code managé. Dans certains cas, le modèle de programmation de ces interfaces n'est également pas intuitif pour les développeurs habitués au .NET Framework.  
  
 Quand vous créez un complément VSTO en utilisant les modèles de projet Office dans Visual Studio, vous n’avez pas à implémenter les interfaces d’extensibilité pour personnaliser des fonctionnalités comme le ruban. Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] les implémente pour vous. Vous pouvez plutôt utiliser les classes et concepteurs plus intuitifs fournis par Visual Studio. Toutefois, vous pouvez quand même implémenter directement les interfaces d’extensibilité dans votre complément VSTO si vous le souhaitez.  
  
 Pour plus d’informations sur les classes et concepteurs que Visual Studio propose pour ces fonctionnalités, consultez [Volets de tâches personnalisés](../vsto/custom-task-panes.md), [Concepteur de ruban](../vsto/ribbon-designer.md) et [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md).  
  
## Interfaces d’extensibilité que vous pouvez implémenter dans un complément VSTO  
 Le tableau suivant répertorie les interfaces d'extensibilité que vous pouvez implémenter et les applications qui les prennent en charge.  
  
|Interface|Description|Applications|  
|---------------|-----------------|------------------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implémentez cette interface pour personnaliser l'interface utilisateur du ruban. **Note:**  Vous pouvez ajouter un élément **Ribbon \(XML\)** à un projet pour générer une implémentation <xref:Microsoft.Office.Core.IRibbonExtensibility> par défaut dans votre complément VSTO. Pour plus d'informations, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projet<br /><br /> Visio<br /><br /> Word|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implémentez cette interface pour créer un volet de tâches personnalisé.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implémentez cette interface pour créer une zone de formulaire Outlook.|Outlook|  
  
 Il existe plusieurs autres interfaces d'extensibilité définies par Microsoft Office, comme <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider> et <xref:Microsoft.Office.Core.SignatureProvider>. Visual Studio ne prend pas en charge l’implémentation de ces interfaces dans un complément VSTO créé à l’aide des modèles de projet Office.  
  
## Utilisation des interfaces d'extensibilité  
 Pour personnaliser une fonctionnalité d’interface utilisateur à l’aide d’une interface d’extensibilité, implémentez l’interface appropriée dans votre projet de complément VSTO. Substituez ensuite la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> pour retourner une instance de la classe qui implémente l'interface.  
  
 Pour obtenir un exemple d’application qui montre comment implémenter les interfaces <xref:Microsoft.Office.Core.IRibbonExtensibility>, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> et <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> dans un complément VSTO pour Outlook, reportez\-vous à l’exemple de gestionnaire d’interface utilisateur dans [Exemples de développement Office](../vsto/office-development-samples.md).  
  
### Exemple d'implémentation d'une interface d'extensibilité  
 L'exemple de code suivant présente une implémentation simple de l'interface <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> pour créer un volet de tâches personnalisé. Cet exemple définit deux classes :  
  
-   La classe `TaskPaneHelper` implémente <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> pour créer et afficher un volet de tâches personnalisé.  
  
-   La classe `TaskPaneUI` fournit l'interface utilisateur du volet de tâches. Les attributs de la classe `TaskPaneUI` rendent la classe visible pour COM, ce qui permet aux applications Microsoft Office de la découvrir. Dans cet exemple, l'interface utilisateur est un <xref:System.Windows.Forms.UserControl> vide, mais vous pouvez ajouter des contrôles en modifiant le code.  
  
    > [!NOTE]  
    >  Pour exposer la classe `TaskPaneUI` à COM, vous devez également définir la propriété **Inscrire pour COM Interop** pour le projet.  
  
 [!code-csharp[Trin_SimpleExtensibilityInterface#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_SimpleExtensibilityInterface#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/VB/ThisAddIn.vb#1)]  
  
 Pour plus d'informations sur l'implémentation de <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, voir [Création de volets de tâches personnalisés Office \(2007\)](http://msdn.microsoft.com/fr-fr/256313db-18cc-496c-a961-381ed9ca94be) dans la documentation de Microsoft Office.  
  
### Exemple de substitution de la méthode RequestService  
 L'exemple de code suivant montre comment substituer la méthode <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> pour retourner une instance de la classe `TaskPaneHelper` de l'exemple de code précédent. Il vérifie la valeur du paramètre *serviceGuid* pour déterminer quelle interface est demandée, puis retourne un objet qui implémente cette interface.  
  
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/VB/ThisAddIn.vb#2)]  
  
## Voir aussi  
 [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Programmation de compléments VSTO](../vsto/programming-vsto-add-ins.md)   
 [Développement de solutions Office](../vsto/developing-office-solutions.md)   
 [Appel de code dans des compléments VSTO à partir d'autres solutions Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
  
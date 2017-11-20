---
title: "Comment : exposer du Code à VBA dans un projet Visual C# | Documents Microsoft"
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
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
ms.assetid: 56d5894b-4823-42f4-8c7e-d8739b859c52
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a52060f1a1b2200109c5003321857915d95bd12a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Comment : exposer du code à VBA dans un projet Visual C#
  Vous pouvez exposer du code dans un projet Visual c# dans Visual Basic pour Applications (VBA) si vous souhaitez que les deux types de code interagissent entre eux.  
  
 Le processus Visual c# est différent du processus Visual Basic. Pour plus d’informations, consultez [Comment : exposer du Code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="exposing-code-in-a-visual-c-project"></a>Exposer du Code dans un projet Visual c#  
 Pour permettre au code VBA d’appeler du code dans un projet Visual c#, modifiez le code afin qu’il est visible par COM et puis définissez la **ReferenceAssemblyFromVbaProject** propriété **True** dans le concepteur.  
  
 Pour une procédure pas à pas qui montre comment appeler une méthode dans un projet Visual c# à partir de VBA, consultez [procédure pas à pas : appel de Code à partir de VBA dans un Visual C &#35; Projet](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
#### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Pour exposer le code dans un projet Visual c# à VBA  
  
1.  Ouvrez ou créez un projet au niveau du document qui est basé sur un document Word, un classeur Excel ou un modèle Excel qui prend en charge les macros et qui contient déjà du code VBA.  
  
     Pour plus d’informations sur les formats de fichier de document qui prennent en charge les macros, consultez [combinaison de VBA et de personnalisations au niveau du Document](../vsto/combining-vba-and-document-level-customizations.md).  
  
    > [!NOTE]  
    >  Cette fonctionnalité ne peut pas être utilisée dans les projets de modèle Word.  
  
2.  Assurez-vous que du code VBA dans le document est autorisé à s’exécuter sans inviter l’utilisateur à activer les macros. Vous pouvez approuver le code VBA à exécuter en ajoutant l'emplacement du projet Office à la liste des emplacements approuvés dans les paramètres du Centre de gestion de la confidentialité pour Word ou Excel.  
  
3.  Ajouter le membre que vous souhaitez exposer à VBA à une classe publique dans votre projet et déclarez le nouveau membre en tant que **public**.  
  
4.  Appliquez ce qui suit <xref:System.Runtime.InteropServices.ComVisibleAttribute> et <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> des attributs à la classe que vous exposez à VBA. Ces attributs rendent la classe visible pour COM, mais ne génèrent pas d'interface de classe.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  Remplacer la **GetAutomationObject** méthode d’une classe d’élément hôte dans votre projet pour retourner une instance de la classe que vous exposez à VBA :  
  
    -   Si vous exposez une classe d’élément hôte à VBA, substituez le **GetAutomationObject** méthode qui appartient à cette classe et retourne l’instance actuelle de la classe.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   Si vous exposez une classe qui n’est pas un élément hôte à VBA, substituez le **GetAutomationObject** élément dans votre projet de méthode de n’importe quel hôte, puis retourner une instance de la classe d’élément non hôte. Par exemple, le code suivant suppose que vous exposez une classe nommée `DocumentUtilities` à VBA.  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     Pour plus d’informations sur les éléments hôtes, consultez [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
6.  Extraire une interface à partir de la classe que vous exposez à VBA. Dans le **extraire l’Interface** boîte de dialogue, sélectionnez les membres publics que vous souhaitez inclure dans la déclaration d’interface. Pour plus d’informations, consultez [refactorisation d’extraction de Interface &#40; C &#35; &#41; ](/visualstudio/csharp-ide/extract-interface-refactoring-csharp).  
  
7.  Ajouter le **public** mot clé à la déclaration d’interface.  
  
8.  Rendre l’interface visible par COM en ajoutant le code suivant <xref:System.Runtime.InteropServices.ComVisibleAttribute> d’attribut à l’interface.  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Ouvrez le document (pour Word) ou une feuille de calcul (pour Excel) dans le concepteur dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. Dans la fenêtre **Propriétés** , sélectionnez la propriété **ReferenceAssemblyFromVbaProject** et remplacez sa valeur par **True**.  
  
    > [!NOTE]  
    >  Si le classeur ou le document ne contient pas déjà du code VBA ou si le code VBA dans le document n’est pas approuvé, vous recevrez un message d’erreur lorsque vous définissez la **ReferenceAssemblyFromVbaProject** propriété **True**. Cela est dû au fait que Visual Studio ne peut pas modifier le projet VBA dans le document dans cette situation.  
  
11. Cliquez sur **OK** dans le message qui s'affiche. Ce message vous rappelle que si vous ajoutez VBA code vers le classeur ou lorsque vous exécutez le projet à partir de documents [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], le code VBA seront perdu lors de la prochaine fois que vous générez le projet. Il s’agit car le document dans la génération de la sortie de dossier est remplacé chaque fois que vous générez le projet.  
  
     À ce stade, Visual Studio configure le projet afin que le projet VBA peut appeler l’assembly. Visual Studio ajoute également une méthode nommée `GetManagedClass` au projet VBA. Vous pouvez appeler cette méthode à partir de n’importe où dans le projet VBA pour accéder à la classe que vous avez exposée à VBA.  
  
12. Générez le projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Conception et création de Solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Procédure pas à pas : Code d’appel à partir de VBA dans un Visual C &#35; Projet](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Guide pratique pour exposer du code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  
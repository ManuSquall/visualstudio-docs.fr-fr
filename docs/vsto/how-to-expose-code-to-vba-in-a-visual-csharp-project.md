---
title: 'Procédure : Exposer du code à VBA dans un C# projet'
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f0b3f004f6aebed6426238a081369c7d50e15f5
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648507"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Procédure : Exposer du code à VBA dans un visuel C# projet
  Vous pouvez exposer du code dans un projet Visual c# pour Visual Basic pour Applications (VBA) si vous souhaitez que les deux types de code pour interagir avec eux.  
  
 Le processus Visual c# est différent du processus Visual Basic. Pour plus d'informations, voir [Procédure : Exposer du code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="expose-code-in-a-visual-c-project"></a>Exposer du code dans un projet Visual c#  
 Pour permettre au code VBA d’appeler du code dans un projet Visual c#, modifiez le code afin qu’il est visible par COM et puis définissez la **ReferenceAssemblyFromVbaProject** propriété **True** dans le concepteur.  
  
 Pour une procédure pas à pas qui montre comment appeler une méthode dans un élément visuel C# projet à partir de VBA, consultez [procédure pas à pas : Appeler du code à partir de VBA dans un Visual C&#35; projet](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Pour exposer le code dans un projet Visual c# à VBA  
  
1. Ouvrez ou créez un projet au niveau du document qui est basé sur un document Word, un classeur Excel ou un modèle Excel qui prend en charge les macros, et qui contient déjà du code VBA.  
  
    Pour plus d’informations sur les formats de fichier de document qui prennent en charge les macros, consultez [combiner de VBA et de personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).  
  
   > [!NOTE]  
   >  Cette fonctionnalité ne peut pas être utilisée dans les projets de modèle Word.  
  
2. Assurez-vous que le code VBA dans le document est autorisé à s’exécuter sans inviter l’utilisateur à activer les macros. Vous pouvez approuver le code VBA à exécuter en ajoutant l'emplacement du projet Office à la liste des emplacements approuvés dans les paramètres du Centre de gestion de la confidentialité pour Word ou Excel.  
  
3. Ajoutez le membre que vous souhaitez exposer à VBA à une classe publique dans votre projet et déclarez le nouveau membre en tant que **public**.  
  
4. Appliquer les éléments suivants <xref:System.Runtime.InteropServices.ComVisibleAttribute> et <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> des attributs à la classe que vous exposez à VBA. Ces attributs rendent la classe visible pour COM, mais ne génèrent pas d'interface de classe.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   [System.Runtime.InteropServices.ClassInterface(  
       System.Runtime.InteropServices.ClassInterfaceType.None)]  
   ```  
  
5. Remplacer le **GetAutomationObject** méthode d’une classe d’élément hôte dans votre projet pour retourner une instance de la classe que vous exposez à VBA :  
  
   - Si vous exposez une classe d’élément hôte à VBA, substituez le **GetAutomationObject** méthode qui appartient à cette classe et retourne l’instance actuelle de la classe.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return this;  
     }  
     ```  
  
   - Si vous exposez une classe qui n’est pas un élément hôte à VBA, substituez le **GetAutomationObject** méthode de n’importe quel hôte d’élément dans votre projet et retourner une instance de la classe d’élément non hôte. Par exemple, le code suivant suppose que vous exposez une classe nommée `DocumentUtilities` à VBA.  
  
     ```csharp  
     protected override object GetAutomationObject()  
     {  
         return new DocumentUtilities();  
     }  
     ```  
  
     Pour plus d’informations sur les éléments hôtes, consultez [éléments hôtes et héberger de vue d’ensemble des contrôles](../vsto/host-items-and-host-controls-overview.md).  
  
6. Extraire une interface à partir de la classe que vous exposez à VBA. Dans le **extraire l’Interface** boîte de dialogue, sélectionnez les membres publics que vous souhaitez inclure dans la déclaration d’interface. Pour plus d’informations, consultez [extraire l’interface (refactorisation)](../ide/reference/extract-interface.md).
  
7. Ajouter le **public** mot clé à la déclaration d’interface.  
  
8. Rendre l’interface visible par COM en ajoutant le code suivant <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribut à l’interface.  
  
   ```csharp  
   [System.Runtime.InteropServices.ComVisible(true)]  
   ```  
  
9. Ouvrez le document (pour Word) ou la feuille de calcul (pour Excel) dans le concepteur dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
10. Dans la fenêtre **Propriétés** , sélectionnez la propriété **ReferenceAssemblyFromVbaProject** et remplacez sa valeur par **True**.  
  
    > [!NOTE]  
    >  Si le classeur ou le document ne contient-elle pas déjà du code VBA ou si le code VBA dans le document n’est pas approuvé, vous recevrez un message d’erreur lorsque vous définissez la **ReferenceAssemblyFromVbaProject** propriété **True**. Cela est dû au fait que Visual Studio ne peut pas modifier le projet VBA dans le document dans cette situation.  
  
11. Cliquez sur **OK** dans le message qui s'affiche. Ce message vous rappelle que si vous ajoutez VBA au classeur de code ou lorsque vous exécutez le projet à partir de documents [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], le code VBA seront perdu lors de la prochaine fois que vous générez le projet. Il s’agit, car le document dans la génération de sortie de dossier est remplacé chaque fois que vous générez le projet.  
  
     À ce stade, Visual Studio configure le projet afin que le projet VBA peut appeler l’assembly. Visual Studio ajoute également une méthode nommée `GetManagedClass` au projet VBA. Vous pouvez appeler cette méthode depuis n’importe où dans le projet VBA pour accéder à la classe que vous avez exposée à VBA.  
  
12. Générez le projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Combiner VBA et personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)   
 [Procédure pas à pas : Appeler du code à partir de VBA dans un Visual C&#35; projet](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [Guide pratique pour Exposer du code à VBA dans un projet Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  
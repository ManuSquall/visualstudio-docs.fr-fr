---
title: 'Comment : exposer du code à VBA dans un projet Visual Basic'
description: Découvrez comment vous pouvez exposer du code dans un projet Visual Basic à du code Visual Basic pour Applications (VBA) si vous souhaitez que les deux types de code interagissent entre eux.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 69ef8b47ac4038b466d0ebf859832bd4363403cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913494"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Comment : exposer du code à VBA dans un projet Visual Basic
  Vous pouvez exposer du code dans un [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projet à du code Visual Basic pour applications (VBA) si vous souhaitez que les deux types de code interagissent les uns avec les autres.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Le processus de Visual Basic est différent du processus Visual C#. Pour plus d’informations, consultez [Comment : exposer du code à VBA dans un projet Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

 Le processus est différent pour le code dans une classe d’élément hôte que pour le code dans d’autres classes :

- [Exposer du code dans une classe d’élément hôte](#HostItemCode)

- [Exposer du code qui n’est pas dans une classe d’élément hôte](#NonHostItem)

## <a name="expose-code-in-a-host-item-class"></a><a name="HostItemCode"></a> Exposer du code dans une classe d’élément hôte
 Pour permettre au code VBA d’appeler Visual Basic code dans une classe d’élément hôte, affectez la valeur **true** à la propriété **EnableVbaCallers** de l’élément hôte.

 Pour obtenir une procédure pas à pas qui montre comment exposer une méthode d’une classe d’élément hôte et comment l’appeler à partir de VBA, consultez [procédure pas à pas : appeler du code à partir de VBA dans un projet Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Pour plus d’informations sur les éléments hôtes, consultez [vue d’ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Pour exposer du code dans un élément hôte à VBA

1. Ouvrez ou créez un projet au niveau [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] du document basé sur un document Word, un classeur Excel ou un modèle Excel qui prend en charge les macros, et qui contient déjà du code VBA.

     Pour plus d’informations sur les formats de fichier de document qui prennent en charge les macros, consultez [combiner des personnalisations VBA et au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Cette fonctionnalité ne peut pas être utilisée dans les projets de modèle Word.

2. Veillez à ce que le code VBA dans le document soit autorisé à s’exécuter sans inviter l’utilisateur à activer les macros. Vous pouvez approuver le code VBA à exécuter en ajoutant l'emplacement du projet Office à la liste des emplacements approuvés dans les paramètres du Centre de gestion de la confidentialité pour Word ou Excel.

3. Ajoutez la propriété, la méthode ou l’événement que vous souhaitez exposer à VBA à l’une des classes d’élément hôte de votre projet, puis déclarez le nouveau membre comme **public**. Le nom de la classe dépend de l’application :

    - Dans un projet Word, la classe d’élément hôte est nommée `ThisDocument` par défaut.

    - Dans un projet Excel, les classes d’élément hôte sont nommées `ThisWorkbook` , `Sheet1` , `Sheet2` et `Sheet3` par défaut.

4. Affectez la valeur **true** à la propriété **EnableVbaCallers** pour l’élément hôte. Cette propriété est disponible dans la fenêtre **Propriétés** lorsque l’élément hôte est ouvert dans le concepteur.

     Une fois que vous avez défini cette propriété, Visual Studio affecte automatiquement à la propriété **ReferenceAssemblyFromVbaProject** la **valeur true**.

    > [!NOTE]
    > Si le classeur ou le document ne contient pas encore de code VBA, ou si l’exécution du code VBA dans le document n’est pas approuvée, vous recevrez un message d’erreur lorsque vous affectez à la propriété **EnableVbaCallers** la **valeur true**. Cela est dû au fait que Visual Studio ne peut pas modifier le projet VBA dans le document dans cette situation.

5. Cliquez sur **OK** dans le message qui s'affiche. Ce message vous rappelle que si vous ajoutez du code VBA au classeur ou au document pendant que vous exécutez le projet à partir de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , le code VBA sera perdu la prochaine fois que vous générerez le projet. Cela est dû au fait que le document dans le dossier de sortie de la génération est remplacé chaque fois que vous générez le projet.

     À ce stade, Visual Studio configure le projet afin que le projet VBA puisse appeler l’assembly. Visual Studio ajoute également une propriété nommée `CallVSTOAssembly` au `ThisDocument` module, `ThisWorkbook` , `Sheet1` , `Sheet2` ou `Sheet3` dans le projet VBA. Vous pouvez utiliser cette propriété pour accéder aux membres publics de la classe que vous avez exposée à VBA.

6. Créez le projet.

## <a name="expose-code-that-is-not-in-a-host-item-class"></a><a name="NonHostItem"></a> Exposer du code qui n’est pas dans une classe d’élément hôte
 Pour permettre au code VBA d’appeler Visual Basic code qui ne se trouve pas dans une classe d’élément hôte, modifiez le code afin qu’il soit visible pour VBA.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Pour exposer du code qui n’est pas dans une classe d’élément hôte à VBA

1. Ouvrez ou créez un projet au niveau [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] du document basé sur un document Word, un classeur Excel ou un modèle Excel qui prend en charge les macros, et qui contient déjà du code VBA.

     Pour plus d’informations sur les formats de fichier de document qui prennent en charge les macros, consultez [combiner des personnalisations VBA et au niveau du document](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Cette fonctionnalité ne peut pas être utilisée dans les projets de modèle Word.

2. Veillez à ce que le code VBA dans le document soit autorisé à s’exécuter sans inviter l’utilisateur à activer les macros. Vous pouvez approuver le code VBA à exécuter en ajoutant l'emplacement du projet Office à la liste des emplacements approuvés dans les paramètres du Centre de gestion de la confidentialité pour Word ou Excel.

3. Ajoutez le membre que vous souhaitez exposer à VBA à une classe publique dans votre projet, puis déclarez le nouveau membre comme **public**.

4. Appliquez les <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributs et suivants <xref:Microsoft.VisualBasic.ComClassAttribute> à la classe que vous exposez à VBA. Ces attributs rendent la classe visible pour VBA.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. Substituez la méthode **GetAutomationObject** d'une classe d'élément hôte de votre projet pour retourner une instance de la classe que vous exposez à VBA. L’exemple de code suivant suppose que vous exposez une classe nommée `DocumentUtilities` à VBA.

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. Ouvrez le document (pour Word) ou le concepteur de feuille de calcul (pour Excel) dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

7. Dans la fenêtre **Propriétés** , sélectionnez la propriété **ReferenceAssemblyFromVbaProject** et remplacez sa valeur par **True**.

    > [!NOTE]
    > Si le classeur ou le document ne contient pas encore de code VBA, ou si l’exécution du code VBA dans le document n’est pas approuvée, vous recevrez un message d’erreur lorsque vous affectez à la propriété **ReferenceAssemblyFromVbaProject** la **valeur true**. Cela est dû au fait que Visual Studio ne peut pas modifier le projet VBA dans le document dans cette situation.

8. Cliquez sur **OK** dans le message qui s'affiche. Ce message vous rappelle que si vous ajoutez du code VBA au classeur ou au document pendant que vous exécutez le projet à partir de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , le code VBA sera perdu la prochaine fois que vous générerez le projet. Cela est dû au fait que le document dans le dossier de sortie de la génération est remplacé chaque fois que vous générez le projet.

     À ce stade, Visual Studio configure le projet afin que le projet VBA puisse appeler l’assembly. Visual Studio ajoute également une méthode nommée `GetManagedClass` au projet VBA. Vous pouvez appeler cette méthode à partir de n’importe où dans le projet VBA pour accéder à la classe que vous avez exposée à VBA.

9. Créez le projet.

## <a name="see-also"></a>Voir aussi
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Combiner VBA et les personnalisations au niveau du document](../vsto/combining-vba-and-document-level-customizations.md)
- [Procédure pas à pas : appel de code à partir de VBA dans un projet Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Comment : exposer du code à VBA dans un projet Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)

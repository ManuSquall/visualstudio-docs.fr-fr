---
title: 'Comment : localiser le balisage ASPX | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 63bd8ee614a78752069002820689a2cc6c0be783
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016283"
---
# <a name="how-to-localize-aspx-markup"></a>Comment : localiser le balisage ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] les pages (. aspx) utilisent généralement des valeurs de chaîne codées en dur. Pour localiser ces chaînes, remplacez-les par des expressions qui référencent des ressources localisées.

## <a name="localize-aspx-markup"></a>Localiser le balisage ASPX

#### <a name="to-localize-aspx-markup"></a>Pour localiser le balisage ASPX

1. Ajoutez des fichiers de ressources distincts : un pour la langue par défaut et un pour chaque langue localisée.

     Si vous localisez uniquement le balisage et non le code, ajoutez un élément de projet de fichier de ressources global. Si vous localisez le code et le balisage, ajoutez un élément de projet de fichier de ressources.

    1. Pour ajouter un fichier de ressources globales, dans **Explorateur de solutions**, ouvrez le menu contextuel d’un élément de projet SharePoint, puis choisissez **Ajouter**  >  **un nouvel élément**. Sous le nœud SharePoint **2010** , choisissez le modèle de **fichier de ressources globales** .

    2. Pour ajouter un fichier de ressources, dans **Explorateur de solutions**, ouvrez le menu contextuel d’un élément de projet SharePoint, puis choisissez **Ajouter**  >  **un nouvel élément**. Sous le nœud **Visual Basic** ou **Visual C#** , choisissez le modèle de **fichier de ressources** .

    > [!NOTE]
    > Veillez à ajouter les fichiers de ressources à un élément de projet SharePoint pour activer la propriété type de déploiement. Cette propriété est requise plus loin dans cette procédure. Si votre solution n’a pas d’élément de projet SharePoint, vous pouvez ajouter un projet SharePoint vide et supprimer son fichier *Elements.xml* par défaut.

2. Donnez au fichier de ressources de langue par défaut le nom de votre choix, ajouté avec une extension *. resx* , par exemple MyAppResources. resx. Utilisez le même nom de base pour chaque fichier de ressources localisé, mais ajoutez la culture [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Par exemple, nommez une ressource localisée allemande *MyAppResources.de-de. resx*.

3. Modifiez la valeur de la propriété **type de déploiement** de chaque fichier de ressources en **AppGlobalResource** pour qu’ils soient déployés sur le dossier du serveur App_GlobalResources.

4. Si vous utilisez les ressources pour localiser le code en plus du balisage ASPX, laissez la valeur de la propriété **action de génération** de chaque fichier en tant que **ressource incorporée**. Si vous utilisez uniquement les fichiers de ressources pour localiser le balisage, vous pouvez éventuellement modifier la valeur de la propriété des fichiers en **contenu**. Pour plus d’informations, consultez [localiser des solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

5. Ouvrez chaque fichier de ressources et ajoutez des chaînes localisées, en utilisant les mêmes ID de chaîne dans chaque fichier.

6. Dans le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] balisage de la page ou du contrôle aspx, remplacez les chaînes codées en dur par des valeurs qui utilisent le format suivant :

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     Par exemple, pour localiser le texte d’un contrôle Label dans une page d’application, vous devez modifier :

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     par celle-ci :

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. Appuyez sur la touche **F5** pour générer et exécuter l’application.

8. Dans SharePoint, modifiez la langue d’affichage par défaut.

     Les chaînes localisées s’affichent dans l’application. Pour afficher les ressources localisées, le serveur SharePoint doit disposer d’un module linguistique qui correspond à la culture du fichier de ressources.

## <a name="see-also"></a>Voir aussi
- [Localiser des solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)
- [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)
- [Comment : localiser du code](../sharepoint/how-to-localize-code.md)

---
title: 'Comment : marquer des contrôles comme des contrôles sécurisés | Microsoft Docs'
description: Marquez les contrôles comme des contrôles sécurisés dans la propriété entrées de contrôle sécurisé d’un élément de projet SharePoint ou dans le concepteur de packages lorsque vous ajoutez un assembly.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 024cd50fc36b84addca11dc3c0f23cdc64fa507d
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304503"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Comment : marquer des contrôles comme des contrôles sécurisés
  Pour la sécurité, SharePoint fait la distinction entre les contrôles Web protégés contre l’injection de scripts et les contrôles Web qui ne le sont pas. Les contrôles protégés, ou *contrôles sécurisés*, sont accessibles aux utilisateurs non approuvés. Vous pouvez marquer des contrôles comme sécurisés dans la propriété entrées de contrôle sécurisé d’un élément de projet SharePoint ou dans le **Concepteur de packages** lorsque vous ajoutez un assembly au package. Pour plus d'informations, consultez la rubrique

- [web.config les paramètres de fichier changent](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) et [inscrivent un assembly de composant WebPart en tant que contrôle sécurisé](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

> [!IMPORTANT]
> Ces procédures sont fournies à titre d’illustration. Marquez les contrôles comme sécurisés uniquement si vous êtes certain qu’ils sont sécurisés.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Marquage de contrôles sécurisés dans la propriété entrées de contrôle sécurisé

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Pour marquer les contrôles comme sécurisés ou non sécurisés dans la propriété entrées de contrôle sécurisé

1. Créer une solution SharePoint avec un projet de composant Visual Web part.

2. Ajoutez deux contrôles au composant WebPart : une zone de texte et un bouton. Laissez les noms à leurs valeurs par défaut, TextBox1 et Button1, respectivement.

3. Ajoutez deux entrées à la propriété entrées de **contrôle sécurisé** du composant WebPart. Pour ce faire, cliquez sur le bouton de sélection (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")) en regard de la propriété **entrées de contrôle sécurisé** dans la fenêtre **Propriétés** .

     La boîte de dialogue **entrées de contrôle sécurisé** s’affiche.

4. Dans la boîte de dialogue **entrées de contrôle sécurisé** , cliquez deux fois sur le bouton **Ajouter** pour ajouter deux entrées de contrôle sécurisé au volet **membres** : un pour le bouton et un pour la zone de texte.

5. Choisissez la première entrée de contrôle sécurisé, puis remplacez la valeur de sa propriété **Safe** par **false**, sa propriété de **nom de type** par **Button1** et la propriété de **script Safe par** **false**.

     Cette étape identifie le contrôle bouton comme un contrôle non sécurisé.

6. Choisissez la deuxième entrée de contrôle sécurisé de la liste. Laissez la valeur de sa propriété **Safe** définie sur **true** et affectez à sa propriété **nom de type** la valeur **TextBox1** et la propriété **protégé par rapport** à la propriété script la valeur **true**.

     Le contrôle Text Box est maintenant marqué comme un contrôle qui est protégé contre l’injection de script.

7. Choisissez le bouton **OK** pour fermer la boîte de dialogue.

## <a name="marking-safe-controls-in-the-package-designer"></a>Marquage de contrôles sécurisés dans le concepteur de packages

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Pour marquer les contrôles comme sécurisés ou non sécurisés dans le concepteur de packages

1. Créer une solution SharePoint avec un projet de composant Visual Web part.

2. Ajoutez deux contrôles au composant WebPart : une zone de texte et un bouton. Laissez les noms à leurs valeurs par défaut, TextBox1 et Button1, respectivement.

     Prenez note de l’espace de noms du contrôle, car il est utilisé ultérieurement.

3. Dans la barre de menus, choisissez **générer**  >  **générer la solution** pour générer le projet.

4. Créez une autre solution SharePoint.

5. Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier *Package. Package* , puis choisissez **ouvrir** pour ouvrir le **Concepteur de packages**.

6. Dans le **Concepteur de packages**, choisissez l’onglet **avancé** .

7. Sous **assemblys supplémentaires**, cliquez sur le bouton **Ajouter** , puis choisissez **Ajouter un assembly existant** dans la liste.

8. Dans la boîte de dialogue **Ajouter un assembly existant** , cliquez sur le bouton de sélection (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")) en regard de **chemin d’accès source**.

9. Choisissez l’assembly de la solution SharePoint que vous avez créée à l’étape 1, puis choisissez le bouton **ouvrir** .

10. Pour cet exemple, laissez l’option **Deployment Target** sur GlobalAssemblyCache.

     Cette étape entraîne le déploiement de l’assembly dans le global assembly cache (GAC) du système. Si vous souhaitez que l’assembly soit déployé dans le dossier de l’application Web (bin), sélectionnez plutôt cette option. Pour plus d’informations, consultez [déploiement d’composants WebPart dans SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

11. Dans la zone **contrôles sécurisés** , choisissez le bouton **cliquez ici pour ajouter un nouvel élément** .

12. Entrez les valeurs des propriétés à partir du tableau suivant.

    |Nom de la propriété|Valeur|
    |-------------------|-----------|
    |Espace de noms|Espace de noms qualifié complet pour le contrôle, tel que **BdcModelProject1. VisualWebPart1**.|
    |Nom de type|Button1|
    |Nom de l'assembly|Un nom d’assembly fort, tel que : Microsoft. Office. SharePoint. ClientExtensions, version = 14.0.0.0, culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Safe|Désactivez la case à cocher **sécurisé** .|
    |Protégé contre les scripts|Laissez la case à cocher **sécuriser contre les scripts** désactivée.|

    > [!NOTE]
    > La valeur nom de l' **assembly** pour les assemblys ajoutés via l’onglet **avancé** du **Concepteur de packages** ne peut pas être un jeton. il doit s’agir d’un assembly avec nom fort. Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100)).

13. Appuyez sur la touche **Tab** pour créer une autre entrée de contrôle sécurisé.

14. Cliquez de nouveau sur le bouton **cliquez ici pour ajouter un nouvel élément** .

15. Entrez les valeurs des propriétés à partir du tableau suivant.

    |Nom de la propriété|Valeur|
    |-------------------|-----------|
    |Espace de noms|Espace de noms qualifié complet pour le contrôle, tel que **BdcModelProject1. VisualWebPart1**.|
    |Nom de type|TextBox1|
    |Nom de l'assembly|Un nom d’assembly fort, tel que : Microsoft. Office. SharePoint. ClientExtensions, version = 14.0.0.0, culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Safe|Activez la case à cocher **sécurisé** .|
    |Protégé contre les scripts|Activez la case à cocher **protégé contre les scripts** .|

16. Choisissez la touche **Tab** , puis choisissez le bouton **OK** pour fermer la boîte de dialogue.

## <a name="see-also"></a>Voir aussi
- [Fournir des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

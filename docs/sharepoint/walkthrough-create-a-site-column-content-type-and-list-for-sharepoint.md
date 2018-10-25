---
title: 'Procédure pas à pas : Créer une colonne de Site, le Type de contenu et la liste pour SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2fb78f5c40a04bb69d2f95d7f872b05e3d501113
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900122"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Procédure pas à pas : Créer une colonne de site, le type de contenu et la liste pour SharePoint
  Les procédures suivantes montrent comment créer des colonnes de site SharePoint personnalisées, ou *champs*, ainsi que d’un type de contenu qui utilise les colonnes de site. Il montre également comment créer une liste qui utilise le nouveau type de contenu.  
  
 Cette procédure pas à pas comprend les tâches suivantes :  
  
- [Création de colonnes de Site personnalisé](#BKMK_CreatingCustSiteCols).  
  
- [Création d’un Type de contenu personnalisé](#BKMK_CreateCustContType).  
  
- [Création d’une liste](#BKMK_CreateList).  
  
- [Création d’une liste](#BKMK_CreateList).  
  
- [Test de l’Application](#BKMK_TestApp).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Windows et SharePoint.
  
-   Visual Studio.  
  
## <a name="create-custom-site-columns"></a>Créer des colonnes de site personnalisé
 Cet exemple crée une liste pour la gestion des patients dans un hôpital. Tout d’abord, vous devez créer un projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et ajouter des colonnes de site, comme suit.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Sur le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **fichier** menu, choisissez **New** > **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez **2010**.  
  
3.  Dans le **modèles** volet, choisissez **projet SharePoint 2010**, modifier le nom du projet à **clinique**, puis choisissez le **OK** bouton.  
  
     Le modèle de projet SharePoint 2010 est un projet vide qui est utilisé dans cet exemple pour contenir les colonnes de site et d’autres éléments de projet qui sont ajoutées plus tard.  
  
4.  Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, entrez l’URL pour le site SharePoint local auquel vous souhaitez ajouter le nouvel élément de champ personnalisé ou utilisez l’emplacement par défaut (`http://<`*Nom_système* `>/)`.  
  
5.  Dans le **quel est le niveau de confiance de cette solution SharePoint ?** section, utilisez la valeur par défaut **déployer en tant que sandboxed solution**.  
  
     Pour plus d’informations sur le bac à sable et les solutions de batterie, consultez [considérations relatives à la solution bac à sable](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Choisissez le **Terminer** bouton. Le projet doit figurer dans **l’Explorateur de solutions**.  
  
#### <a name="to-add-site-columns"></a>Pour ajouter des colonnes de site  
  
1.  Ajouter une nouvelle colonne de site. Pour ce faire, dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **clinique**, puis choisissez **ajouter** > **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **colonne de Site**, remplacez le nom par **nom du Patient**, puis choisissez le **ajouter** bouton.  
  
3.  Dans de la colonne site *Elements.xml* fichier, laissez le **Type** en **texte**et de modifier le **groupe** à  **Cours pratique les colonnes de Site**. Lorsque vous avez terminé, la colonne de site *Elements.xml* fichier doit se présenter comme dans l’exemple suivant.  
  
    ```xml  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  À l’aide de la même procédure, ajoutez deux colonnes de site supplémentaires au projet : **ID de Patient** (Type = « Integer ») et **nom médecin** (Type = « Text »). La valeur est la valeur de leur groupe **les colonnes de Site stage**.  
  
## <a name="create-a-custom-content-type"></a>Créer un type de contenu personnalisé
 Ensuite, créez un type de contenu, en fonction du type de contenu de Contacts, qui inclut les colonnes de site que vous avez créé dans la procédure précédente. À partir d’un type de contenu sur un type de contenu existant, vous pouvez gagner du temps, car le type de contenu de base fournit plusieurs colonnes de site à utiliser dans le nouveau type de contenu.  
  
#### <a name="to-create-a-custom-content-type"></a>Pour créer un type de contenu personnalisé  
  
1.  Ajouter un type de contenu au projet. Pour ce faire, dans **l’Explorateur de solutions**, choisissez le nœud du projet  
  
2.  Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.  
  
3.  Sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
4.  Dans le **modèles** volet, choisissez le **Type de contenu** modèle, remplacez le nom par **données patient**, puis choisissez le **ajouter** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’ouvre.  
  
5.  Dans le **le type de contenu de base ce type de contenu doit hériter de** , choisissez **Contact** comme type de contenu sur lequel baser le nouveau type de contenu, puis choisissez le **Terminer**bouton.  
  
     Cela vous donne accès à d’autres colonnes de site pouvant s’avérer utiles dans le type de contenu de Contact, en plus des colonnes de site que vous avez défini précédemment.  
  
6.  Après le Type de contenu concepteur s’affiche, dans le **colonnes** onglet, ajoutez les trois colonnes que vous avez défini précédemment de site : **nom du Patient**, **ID de Patient**et **Nom médecin**. Pour ajouter ces colonnes, choisissez la première zone de liste dans la liste de colonnes de site sous **nom d’affichage**, puis choisissez chaque colonne de site dans la liste un à la fois.  
  
    > [!TIP]  
    >  Pour choisir les colonnes de site plus rapidement, filtrer la liste en tapant les premières lettres du nom de la colonne.  
  
7.  Outre les trois colonnes de site personnalisé, ajoutez le **commentaires** colonne de site à partir de la liste de colonnes de site.  
  
8.  Sélectionnez le **requis** case à cocher pour le **nom du Patient** et **ID de Patient** des colonnes de site pour les rendre les champs requis.  
  
9. Sur le **Content Type** onglet, assurez-vous que le nom de type de contenu est **données patient**, puis modifiez la description à **carte d’informations sur les patients**.  
  
10. Modification **nom_groupe** à **les Types de contenu clinique**et laissez les autres paramètres à leurs valeurs par défaut.  
  
11. Dans la barre de menus, choisissez **fichier** > **Enregistrer tout**, puis fermez le Concepteur de Type de contenu.  
  
## <a name="create-a-list"></a>Créer une liste
 Maintenant, créez une liste qui utilise les nouvelles colonnes type de contenu de site.  
  
#### <a name="to-create-a-list"></a>Pour créer une liste  
  
1.  Ajouter une liste au projet. Pour ce faire, dans **l’Explorateur de solutions**, choisissez le nœud du projet.  
  
2.  Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.  
  
3.  Sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
4.  Dans le **modèles** volet, choisissez le **liste** modèle, remplacez le nom par **Patients**, puis choisissez le **ajouter** bouton.  
  
5.  Laissez le **personnaliser la liste en fonction** définissant en tant que **par défaut (vide)**, puis choisissez le **Terminer** bouton.  
  
6.  Dans le Concepteur de la liste, choisissez le **Types de contenu** bouton pour afficher la **des paramètres de Type de contenu** boîte de dialogue.  
  
7.  Cliquez sur la nouvelle ligne, choisissez le **données patient** type dans la liste des types de contenu de contenu, puis choisissez le **OK** bouton.  
  
     Cette opération ajoute toutes les colonnes de site à partir de la **données patient** type dans la liste de contenu.  
  
8.  Supprimer toutes les colonnes de site dans la liste à l’exception de ce qui suit :  
  
    -   Identification de patient  
  
    -   Nom du patient  
  
    -   Numéro de téléphone personnel  
  
    -   Courrier électronique  
  
    -   Nom du Doctor  
  
    -   Commentaires  
  
9. Sous **colonne surnom**, choisissez une ligne vide, ajoutez une colonne de liste personnalisée et nommez-le **hôpital**. Laissez son type de données en tant que **seule ligne de texte**.  
  
     La colonne de liste personnalisée s’applique uniquement à cette liste. Lorsque vous ajoutez une colonne de liste personnalisé à une liste, un nouvelle liste type de contenu, y compris toutes les colonnes ajoutées à la liste, est créé et défini en tant que la liste par défaut.  
  
    > [!TIP]  
    >  Si vous choisissez une colonne dans la liste des colonnes de site, une colonne de site existante est utilisée. Toutefois, si vous entrez une valeur de nom de colonne sans choisir toutes les colonnes dans la liste, une colonne de liste personnalisée est créée, même si une colonne portant le même nom existe déjà dans la liste.  
  
     Si vous le souhaitez, au lieu de la définition du type de données de la colonne de liste personnalisée pour **seule ligne de texte**, vous pouvez à la place définir le type de données pour cette colonne de recherche et ses valeurs seraient récupérées à partir d’une table ou une autre liste. Pour plus d’informations sur les colonnes de recherche, consultez [des relations de liste dans SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) et [recherches et des relations de liste](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Regard le **ID de Patient** et **nom du Patient** zones, sélectionnez le **requis** case à cocher.  
  
11. Sur le **vues** , choisir une ligne vide pour créer une vue. Entrez **les détails des patients**.  
  
     Sur le **vues** onglet, vous pouvez spécifier les colonnes que vous souhaitez voir apparaître dans la liste SharePoint.  
  
12. Choisissez la nouvelle **Patient détails** de ligne, puis choisissez le **définir comme valeur par défaut** bouton.  
  
     La nouvelle vue est désormais la vue par défaut pour la liste.  
  
13. Ajoutez les colonnes suivantes à la **colonnes sélectionnées** liste dans l’ordre suivant :  
  
    -   Identification de patient  
  
    -   Nom du patient  
  
    -   Numéro de téléphone personnel  
  
    -   Courrier électronique  
  
    -   Nom du Doctor  
  
    -   Hôpital  
  
    -   Commentaires  
  
14. Dans le **propriétés** , choisissez le **tri et regroupement** propriété, puis choisissez le bouton de sélection ![icône des points de suspension](../sharepoint/media/ellipsisicon.gif "points de suspension")pour afficher le **tri et regroupement** boîte de dialogue.  
  
15. Dans le **nom de colonne** , choisissez **Patient nom**, assurez-vous que le **tri** colonne est définie sur **croissant**, puis choisissez le  **OK** bouton.  
  
## <a name="test-the-application"></a>Tester l’application
 Maintenant que les colonnes de site personnalisées, type de contenu et liste sont prêts, les déployer sur SharePoint et exécuter l’application à tester.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Dans la barre de menus, sélectionnez **Fichier** > **Enregistrer tout**.  
  
2.  Choisissez le **F5** touche pour exécuter l’application.  
  
     L’application est compilée, et ses fonctionnalités sont déployées sur SharePoint, puis activées.  
  
3.  Dans la barre de Navigation rapide, choisissez le **Patients** lien pour afficher le **Patients** liste.  
  
     Les noms de colonnes dans la liste doivent correspondre à ceux que vous avez entré sur le **vues** onglet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Choisissez le **ajouter un nouvel élément** lien pour créer une carte d’informations sur les patients.  
  
5.  Entrez les informations dans les champs, puis choisissez le **enregistrer** bouton.  
  
     Le nouvel enregistrement apparaît dans la liste.  
  
## <a name="see-also"></a>Voir aussi
 [Créer des colonnes de site, les types de contenu et listes pour SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Comment : créer un Type de champ personnalisé](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Types de contenu](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Colonnes](http://go.microsoft.com/fwlink/?LinkId=192081)  
  

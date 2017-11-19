---
title: "Procédure pas à pas : Créer une colonne de Site, le Type de contenu et la liste pour SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: caebacc2-616c-4373-8e21-edc7979338e7
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d6007dee14f89f875c66009f048b47579e97028b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Procédure pas à pas : création d'une colonne de site, d'un type de contenu et d'une liste pour SharePoint
  Les procédures suivantes montrent comment créer des colonnes de site SharePoint personnalisées, ou *champs*, ainsi que d’un type de contenu qui utilise les colonnes de site. Il montre également comment créer une liste qui utilise le type de contenu.  
  
 Cette procédure pas à pas comprend les tâches suivantes :  
  
-   [Création de colonnes de Site personnalisé](#BKMK_CreatingCustSiteCols).  
  
-   [Création d’un Type de contenu personnalisé](#BKMK_CreateCustContType).  
  
-   [Création d’une liste](#BKMK_CreateList).  
  
-   [Création d’une liste](#BKMK_CreateList).  
  
-   [Test de l’Application](#BKMK_TestApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Éditions prises en charge de Windows et SharePoint. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
##  <a name="BKMK_CreatingCustSiteCols"></a>Création de colonnes de Site personnalisé  
 Cet exemple crée une liste de gestion des patients dans un hôpital. Tout d’abord, vous devez créer un projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et ajouter des colonnes de site, comme suit.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Sur le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **fichier** menu, choisissez **nouveau**, **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez **2010**.  
  
3.  Dans le **modèles** volet, choisissez **projet SharePoint 2010**, modifier le nom du projet pour **Clinic**, puis choisissez le **OK** bouton.  
  
     Le modèle de projet SharePoint 2010 est un projet vide qui est utilisé dans cet exemple pour contenir les colonnes de site et d’autres éléments de projet qui sont ajoutées plus tard.  
  
4.  Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, entrez l’URL du site SharePoint local auquel vous souhaitez ajouter le nouvel élément de champ personnalisé ou utilisez l’emplacement par défaut (`http://<`*Nom_système* `>/)`.  
  
5.  Dans le **quel est le niveau de confiance de cette solution SharePoint ?** section, utilisez la valeur par défaut **déployer comme une solution bac à sable**.  
  
     Pour plus d’informations sur le bac à sable et les solutions de batterie, consultez [considérations sur les solutions bac à sable](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Choisissez le **Terminer** bouton. Le projet doit maintenant être affiché dans **l’Explorateur de solutions**.  
  
#### <a name="to-add-site-columns"></a>Pour ajouter des colonnes de site  
  
1.  Ajouter une nouvelle colonne de site. Pour ce faire, dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **Clinic**, puis choisissez **ajouter**, **un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, choisissez **colonne de Site**, remplacez le nom par **nom du Patient**, puis choisissez le **ajouter** bouton.  
  
3.  Dans le fichier Elements.xml de la colonne de site, laissez le **Type** définition en tant que **texte**et modifier le **groupe** à **cours pratique des colonnes de Site**. Lorsque vous avez terminé, le fichier Elements.xml de la colonne de site doit ressembler à l’exemple suivant.  
  
    ```  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  À l’aide de la même procédure, ajoutez deux colonnes de site supplémentaires au projet : **ID du Patient** (Type = « Integer ») et **nom médecin** (Type = « Text »). Valeur leur groupe **cours pratique des colonnes de Site**.  
  
##  <a name="BKMK_CreateCustContType"></a>Création d’un Type de contenu personnalisé  
 Ensuite, créez un type de contenu, en fonction du type de contenu de Contacts, qui inclut les colonnes de site que vous avez créé dans la procédure précédente. À partir d’un type de contenu sur un type de contenu existant, vous pouvez gagner du temps, car le type de contenu de base fournit plusieurs colonnes de site à utiliser dans le nouveau type de contenu.  
  
#### <a name="to-create-a-custom-content-type"></a>Pour créer un type de contenu personnalisé  
  
1.  Ajouter un type de contenu au projet. Pour ce faire, dans **l’Explorateur de solutions**, choisissez le nœud du projet  
  
2.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
3.  Sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
4.  Dans le **modèles** volet, choisissez le **Type de contenu** modèle, remplacez le nom par **Patient Info**, puis choisissez le **ajouter** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’ouvre.  
  
5.  Dans le **le type de contenu de base ce type de contenu doit hériter de** , choisissez **Contact** comme type de contenu sur lequel baser le nouveau type de contenu, puis choisissez le **Terminer**bouton.  
  
     Cela vous permet d’accéder à d’autres colonnes de site peuvent se révéler utiles dans le type de contenu de Contact, en plus des colonnes de site que vous avez défini précédemment.  
  
6.  Après le Type de contenu concepteur s’affiche, dans le **colonnes** onglet, ajoutez les trois colonnes que vous avez défini précédemment de site : **nom du Patient**, **ID du Patient**et **Nom médecin**. Pour ajouter ces colonnes, choisissez la zone de liste dans la liste de colonnes de site sous **nom d’affichage**, puis choisissez la colonne de chaque site dans la liste une à la fois.  
  
    > [!TIP]  
    >  Pour choisir les colonnes de site plus rapidement, filtrez la liste en tapant les premières lettres du nom de la colonne.  
  
7.  Outre les trois colonnes de site personnalisé, ajoutez le **commentaires** colonne de site à partir de la liste de colonnes de site.  
  
8.  Sélectionnez le **requis** case à cocher pour le **nom du Patient** et **ID du Patient** des colonnes de site pour les rendre les champs obligatoires.  
  
9. Sur le **Content Type** onglet, vérifiez que le nom de type de contenu est **données patient**, puis modifiez la description pour **fiche d’informations sur les patients**.  
  
10. Modification **nom de groupe** à **les Types de contenu Clinic**et conservez les autres paramètres à leurs valeurs par défaut.  
  
11. Dans la barre de menus, choisissez **fichier**, **Enregistrer tout**, puis fermez le Concepteur de Type de contenu.  
  
##  <a name="BKMK_CreateList"></a>Création d’une liste  
 À présent, créez une liste qui utilise les nouvelles colonnes type de contenu de site.  
  
#### <a name="to-create-a-list"></a>Pour créer une liste  
  
1.  Ajouter une liste au projet. Pour ce faire, dans **l’Explorateur de solutions**, choisissez le nœud du projet.  
  
2.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
3.  Sous **Visual C#** ou **Visual Basic**, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
4.  Dans le **modèles** volet, choisissez la **liste** modèle, remplacez le nom par **Patients**, puis choisissez le **ajouter** bouton.  
  
5.  Laissez le **personnaliser la liste en fonction de** définition en tant que **par défaut (vide)**, puis choisissez le **Terminer** bouton.  
  
6.  Dans le Concepteur de la liste, choisissez la **Types de contenu** bouton pour afficher la **des paramètres de Type de contenu** boîte de dialogue.  
  
7.  Cliquez sur la nouvelle ligne, choisissez le **données patient** type dans la liste des types de contenu de contenu, puis choisissez le **OK** bouton.  
  
     Cette opération ajoute toutes les colonnes de site à partir de la **données patient** type dans la liste de contenu.  
  
8.  Supprimer toutes les colonnes de site dans la liste à l’exception des opérations suivantes :  
  
    -   Identification de patient  
  
    -   Nom du patient  
  
    -   Téléphone personnel  
  
    -   Courrier électronique  
  
    -   Nom médecin  
  
    -   Commentaires  
  
9. Sous **nom complet de la colonne**, choisissez une ligne vide, ajoutez une colonne de liste personnalisée et nommez-le **hôpital**. Conserver son type de données en tant que **ligne unique de texte**.  
  
     La colonne de liste personnalisée s’applique uniquement à cette liste. Lorsque vous ajoutez une colonne de liste personnalisée à une liste, un nouvelle liste type de contenu, y compris toutes les colonnes ajoutées à la liste, est créé et défini en tant que la liste par défaut.  
  
    > [!TIP]  
    >  Si vous choisissez une colonne dans la liste des colonnes de site, une colonne de site existante est utilisée. Toutefois, si vous entrez une valeur de nom de colonne sans choisir des colonnes dans la liste, une colonne de liste personnalisée est créée, même si une colonne portant le même nom existe déjà dans la liste.  
  
     Si vous le souhaitez, au lieu de la définition du type de données de la colonne de liste personnalisée pour **ligne unique de texte**, vous pouvez définir à la place de type de données pour cette colonne pour la recherche et ses valeurs sont extrait à partir d’une table ou une autre liste. Pour plus d’informations sur les colonnes de recherche, consultez [des relations de liste dans SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) et [recherches et des relations de liste](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. À côté du **ID du Patient** et **nom du Patient** zones, sélectionnez le **requis** case à cocher.  
  
11. Sur le **vues** onglet, cliquez sur une ligne vide pour créer une vue. Entrez **les détails des patients**.  
  
     Sur le **vues** onglet, vous pouvez spécifier les colonnes que vous souhaitez voir apparaître dans la liste SharePoint.  
  
12. Choisissez le nouveau **Patient détails** de ligne, puis choisissez le **définie comme valeur par défaut** bouton.  
  
     La nouvelle vue est désormais la vue par défaut pour la liste.  
  
13. Ajoutez les colonnes suivantes à la **colonnes sélectionnées** liste dans l’ordre suivant :  
  
    -   Identification de patient  
  
    -   Nom du patient  
  
    -   Téléphone personnel  
  
    -   Courrier électronique  
  
    -   Nom médecin  
  
    -   Hôpital  
  
    -   Commentaires  
  
14. Dans le **propriétés** , choisissez le **tri et regroupement** propriété, puis choisissez le bouton de sélection ![icône des points de suspension](../sharepoint/media/ellipsisicon.gif "icône de points de suspension")pour afficher les **tri et regroupement** boîte de dialogue.  
  
15. Dans le **nom de la colonne** , choisissez **nom du Patient**, vous assurer que le **tri** colonne a la valeur **croissant**, puis choisissez le  **OK** bouton.  
  
##  <a name="BKMK_TestApp"></a>Test de l’Application  
 Maintenant que les colonnes de site personnalisées, le type de contenu et la liste prêts, les déployer sur SharePoint et exécuter l’application à tester.  
  
#### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Enregistrer tout**.  
  
2.  Appuyez sur la touche F5 pour exécuter l'application.  
  
     L’application est compilée, et ensuite ses fonctionnalités sont déployées sur SharePoint et activées.  
  
3.  Dans la barre de Navigation rapide, choisissez le **Patients** lien pour afficher le **Patients** liste.  
  
     Les noms de colonnes dans la liste doivent correspondre à ceux que vous avez entrés dans le **vues** onglet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Choisissez le **ajouter un nouvel élément** lien pour créer une carte d’informations sur les patients.  
  
5.  Entrez les informations dans les champs, puis choisissez le **enregistrer** bouton.  
  
     Le nouvel enregistrement apparaît dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de colonnes de Site, les Types de contenu et listes pour SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Comment : créer un Type de champ personnalisé](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Types de contenu](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Colonnes](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  
---
title: Créer une colonne de site, un type de contenu et une liste pour SharePoint
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 041c0ba5174450fca7acf7247b1cf40a98ac147d
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298377"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Procédure pas à pas : création d’une colonne de site, d’un type de contenu et d’une liste pour SharePoint
  Les procédures suivantes montrent comment créer des colonnes de site SharePoint personnalisées, ou des *champs*, ainsi qu’un type de contenu qui utilise les colonnes de site. Il montre également comment créer une liste qui utilise le nouveau type de contenu.

 Cette procédure pas à pas comprend les tâches suivantes :

- [Créer des colonnes de site personnalisées](#create-custom-site-columns).

- [Créez un type de contenu personnalisé](#create-a-custom-content-type).

- [Créer une liste](#create-a-list).

- [Testez l’application](#test-the-application).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de Windows et SharePoint.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Créer des colonnes de site personnalisées
 Cet exemple crée une liste pour la gestion des patients dans un hôpital. Tout d’abord, vous devez créer un projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et y ajouter des colonnes de site, comme suit.

#### <a name="to-create-the-project"></a>Pour créer le projet

1. Dans le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] menu **fichier** , choisissez **nouveau**  >  **projet**.
::: moniker range="=vs-2017"
2. Dans la boîte de dialogue **nouveau projet** , sous **Visual C#** ou **Visual Basic**, développez le nœud **Office/SharePoint** , puis sélectionnez **solutions SharePoint**.

3. Dans le volet **modèles** , choisissez le **projet SharePoint vide** pour la version particulière de SharePoint que vous avez installée. Par exemple, si vous avez SharePoint 2016 installer, sélectionnez le modèle **de projet sharepoint 2016-vide** .  

4. Remplacez le nom du projet par **Clinic**, puis choisissez le bouton **OK** .

5. Dans la boîte de dialogue **spécifier le site et le niveau de sécurité pour le débogage** , entrez l’URL du site SharePoint local auquel vous souhaitez ajouter le nouvel élément de champ personnalisé ou utilisez l’emplacement par défaut ( `http://<` *SystemName* `>/)` .

6. Dans la section **qu’est-ce que le niveau de confiance pour cette solution SharePoint ?** , utilisez la valeur par défaut **déployer en tant que solution bac à sable (sandbox)**.

     Pour plus d’informations sur les solutions sandbox et de batterie de serveurs, consultez Considérations sur les [solutions bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md).

7. Cliquez sur le bouton **Terminer**. Le projet est maintenant listé dans **Explorateur de solutions**.
::: moniker-end
::: moniker range=">=vs-2019"
2.  Dans la boîte de dialogue **créer un nouveau projet** , sélectionnez le **projet SharePoint vide** pour la version particulière de SharePoint que vous avez installée. Par exemple, si vous avez SharePoint 2016 installer, sélectionnez le modèle **de projet sharepoint 2016-vide** .
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Remplacez le nom du projet par **Clinic**, puis choisissez le bouton **créer** .

4. Dans la boîte de dialogue **spécifier le site et le niveau de sécurité pour le débogage** , entrez l’URL du site SharePoint local auquel vous souhaitez ajouter le nouvel élément de champ personnalisé ou utilisez l’emplacement par défaut ( `http://<` *SystemName* `>/)` .

5. Dans la section **qu’est-ce que le niveau de confiance pour cette solution SharePoint ?** , utilisez la valeur par défaut **déployer en tant que solution bac à sable (sandbox)**.

     Pour plus d’informations sur les solutions sandbox et de batterie de serveurs, consultez Considérations sur les [solutions bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md).

6. Cliquez sur le bouton **Terminer**. Le projet est maintenant listé dans **Explorateur de solutions**.
::: moniker-end

#### <a name="to-add-site-columns"></a>Pour ajouter des colonnes de site

1. Ajoutez une nouvelle colonne de site. Pour ce faire, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **Clinic** , puis choisissez **Ajouter**  >  **un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **colonne de site**, changez le nom en **PatientName**, puis cliquez sur le bouton **Ajouter** .

3. Dans le fichier *Elements.xml* de la colonne de site, laissez le paramètre de **type** **texte**, puis modifiez le paramètre de **groupe** en **colonnes de site Clinic**. Lorsque vous avez terminé, le fichier *Elements.xml* de la colonne de site doit ressembler à l’exemple suivant.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="PatientName"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

    > [!TIP]
    > Si vous utilisez la casse mixte dans le nom de la colonne de site, Visual Studio ajoute automatiquement un espace dans DisplayName.
    > Il est recommandé de ne pas utiliser d’espaces dans le nom de colonne de site, car cela peut entraîner des problèmes lorsque vous essayez de déployer la solution sur SharePoint.

4. À l’aide de la même procédure, ajoutez deux colonnes de site supplémentaires au projet : **patient** (type = "Integer") et **DoctorName** (type = "Text"). Définissez leur valeur de groupe sur les **colonnes de site Clinic**.

## <a name="create-a-custom-content-type"></a>Créer un type de contenu personnalisé
 Ensuite, créez un type de contenu, basé sur le type de contenu contacts, qui comprend les colonnes de site que vous avez créées au cours de la procédure précédente. En basant un type de contenu sur un type de contenu existant, vous pouvez gagner du temps, car le type de contenu de base fournit plusieurs colonnes de site à utiliser dans le nouveau type de contenu.

#### <a name="to-create-a-custom-content-type"></a>Pour créer un type de contenu personnalisé

1. Ajoutez un type de contenu au projet. Pour ce faire, dans **Explorateur de solutions**, choisissez le nœud du projet.

2. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

3. Sous **Visual C#** ou **Visual Basic**, développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

4. Dans le volet **modèles** , choisissez le modèle de **type de contenu** , remplacez le nom par **patient info**, puis cliquez sur le bouton **Ajouter** .

     L' **Assistant Personnalisation de SharePoint** s’ouvre.

5. Dans la liste quel type de contenu de **base doit hériter de ce type de contenu** , choisissez **contact** comme type de contenu sur lequel baser le nouveau type de contenu, puis choisissez le bouton **Terminer** .

     Cela vous permet d’accéder à d’autres colonnes de site potentiellement utiles dans le type de contenu contact, en plus des colonnes de site que vous avez définies précédemment.

6. Une fois le concepteur de types de contenu affiché, dans l’onglet **colonnes** , ajoutez les trois colonnes de site que vous avez définies précédemment : **nom du patient**, **ID du patient**et nom du **médecin**. Pour ajouter ces colonnes, choisissez la première zone de liste dans la liste colonnes de site sous **nom complet**, puis choisissez chaque colonne de site dans la liste une par une.

    > [!TIP]
    > Pour choisir les colonnes de site plus rapidement, filtrez la liste en entrant les premières lettres du nom de la colonne.

7. En plus des trois colonnes de site personnalisées, ajoutez la colonne de site **Commentaires** à partir de la liste colonnes de site.

8. Activez la case à cocher **requis** pour les colonnes de site **nom du patient** et ID du **patient** pour les rendre obligatoires.

9. Dans l’onglet **type de contenu** , assurez-vous que le nom du type de contenu est informations sur le **patient**, puis modifiez la description en **carte d’informations sur les patients**.

10. Modifiez **nom du groupe** en **types de contenu Clinic**et laissez les autres paramètres à leurs valeurs par défaut.

11. Dans la barre de menus, choisissez **fichier**  >  **enregistrer tout**, puis fermez le concepteur de types de contenu.

## <a name="create-a-list"></a>Créer une liste
 À présent, créez une liste qui utilise le nouveau type de contenu et les nouvelles colonnes de site.

#### <a name="to-create-a-list"></a>Pour créer une liste

1. Ajoutez une liste au projet. Pour ce faire, dans **Explorateur de solutions**, choisissez le nœud du projet.

2. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

3. Sous **Visual C#** ou **Visual Basic**, développez le nœud **SharePoint** .

4. Dans le volet **modèles** , choisissez le modèle de **liste** , remplacez le nom par **patients**, puis cliquez sur le bouton **Ajouter** .

5. Laissez la liste **personnaliser la liste en fonction** du paramètre **par défaut (liste personnalisée)**, puis choisissez le bouton **Terminer** .

6. Dans le concepteur de listes, choisissez le bouton **types de contenu** pour afficher la boîte de dialogue Paramètres du **type de contenu** .

7. Choisissez la nouvelle ligne, choisissez le type de contenu informations sur le **patient** dans la liste des types de contenu, puis choisissez le bouton **OK** .

     Cela permet d’ajouter toutes les colonnes de site du type de contenu **informations sur le patient** à la liste.

8. Supprimez toutes les colonnes de site de la liste, à l’exception des suivantes :

    - ID du patient

    - Nom du patient

    - Téléphone personnel

    - Courrier électronique

    - Nom du médecin

    - Commentaires

9. Sous **nom d’affichage**de la colonne, choisissez une ligne vide, ajoutez une colonne de liste personnalisée et nommez-la **hospitalier**. Laissez son type de données **une seule ligne de texte**.

     La colonne de liste personnalisée s’applique uniquement à cette liste. Lorsque vous ajoutez une colonne de liste personnalisée à une liste, un nouveau type de contenu de liste, y compris toutes les colonnes ajoutées à la liste, est créé et défini comme liste par défaut.

    > [!TIP]
    > Si vous choisissez une colonne dans la liste des colonnes de site, une colonne de site existante est utilisée. Toutefois, si vous entrez une valeur de nom de colonne sans sélectionner de colonnes dans la liste, une colonne de liste personnalisée est créée, même si une colonne portant le même nom existe déjà dans la liste.

     Si vous le souhaitez, au lieu de définir le type de données de la colonne de liste personnalisée sur une **seule ligne de texte**, vous pouvez définir le type de données de cette colonne sur Lookup, et ses valeurs sont extraites d’une table ou d’une autre liste. Pour plus d’informations sur les colonnes de recherche, consultez [répertorier les relations dans SharePoint 2010](/previous-versions/msp-n-p/ff798514(v=pandp.10)) et les [recherches et relations de liste](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14)).

10. En regard des zones **ID du patient** et nom du **patient** , activez la case à cocher **requis** .

11. Sous l’onglet **vues** , choisissez une ligne vide pour créer une vue. Entrez les **Détails des patients** dans une ligne vide sous la colonne nom de la **vue** .

     Dans l’onglet **affichages** , vous pouvez spécifier les colonnes que vous souhaitez voir apparaître dans la liste SharePoint.

12. Choisissez la nouvelle ligne **Détails du patient** , puis choisissez le bouton **définir comme valeur par défaut** .

     La nouvelle vue est désormais l’affichage par défaut de la liste.

13. Ajoutez les colonnes suivantes à la liste **colonnes sélectionnées** dans l’ordre suivant :

    - ID du patient

    - Nom du patient

    - Téléphone personnel

    - Courrier électronique

    - Nom du médecin

    - Hôpitaux

    - Commentaires

14. Dans la liste **Propriétés** , choisissez la propriété de **Tri et de regroupement** , puis cliquez sur l’icône de ![points](../sharepoint/media/ellipsisicon.gif "Icône du bouton de sélection (...)") de suspension du bouton de sélection pour afficher la boîte de dialogue de **Tri et de regroupement** .

15. Dans la liste **nom** de la colonne, choisissez **nom du patient**, assurez-vous que la colonne de **Tri** est définie sur **croissant**, puis choisissez le bouton **OK** .

## <a name="test-the-application"></a>Test de l’application
 Maintenant que les colonnes de site personnalisées, le type de contenu et la liste sont prêts, déployez-les sur SharePoint et exécutez l’application pour la tester.

#### <a name="to-test-the-application"></a>Pour tester l'application

1. Dans la barre de menus, choisissez **fichier**  >  **enregistrer tout**.

2. Appuyez sur la touche **F5** pour exécuter l’application.

     L’application est compilée, puis ses fonctionnalités sont déployées sur SharePoint et activées.

3. Dans la barre de navigation rapide, choisissez le lien **patients** pour afficher la liste des **patients** .

     Les noms de colonnes de la liste doivent correspondre à ceux que vous avez entrés dans l’onglet **affichages** dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

4. Choisissez le lien **Ajouter un nouvel élément** pour créer une carte d’informations sur les patients.

5. Entrez les informations dans les champs, puis cliquez sur le bouton **Enregistrer** .

     Le nouvel enregistrement apparaît dans la liste.

## <a name="see-also"></a>Voir aussi
- [Créer des colonnes de site, des types de contenu et des listes pour SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Comment : créer un type de champ personnalisé](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [Types de contenu](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [Colonnes](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))

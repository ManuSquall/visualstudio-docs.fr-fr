---
title: 'Procédure pas à pas : importer un flux de travail réutilisable SharePoint Designer | Microsoft Docs'
titleSuffix: ''
description: Dans cette procédure pas à pas, importez un flux de travail réutilisable créé dans SharePoint Designer dans un projet de flux de travail SharePoint Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1421b061c50277177b5a30f0357725e9a042f3bd
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970190"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow"></a>Procédure pas à pas : importer un flux de travail réutilisable SharePoint Designer

  Cette procédure pas à pas montre comment importer un flux de travail réutilisable créé dans SharePoint Designer 2010 dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet de flux de travail SharePoint.

 Les flux de travail créés dans SharePoint Designer, ou les *flux de travail déclaratifs*, consistent en des [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instructions au lieu de code. SharePoint Designer 2010 présente des *flux de travail réutilisables*, qui sont des flux de travail déclaratifs portables qui peuvent être utilisés par différentes listes dans les sites SharePoint.

 Les flux de travail créés dans [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , tels que les workflows de machine d’État et séquentiels, sont appelés *workflows de code*. Les flux de travail de code consistent en des fichiers XML et des modules de code dans lesquels les utilisateurs peuvent personnaliser le comportement du flux de travail.

 Visual Studio vous permet d'importer des flux de travail réutilisables créés dans SharePoint Designer 2010 et de les convertir sous forme de flux de travail avec code en vue de les exploiter sur vos sites SharePoint.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un flux de travail simple et réutilisable dans SharePoint Designer.

- Exportation du flux de travail réutilisable SharePoint Designer dans un fichier *. wsp* et dans SharePoint.

- Importation du fichier *. wsp* dans à [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] l’aide du projet importer le flux de travail réutilisable.

- Modification du flux de travail en ajoutant du code.

- Utilisation du flux de travail importé dans un site SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Éditions prises en charge de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint.

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Créer des sous-sites SharePoint cibles
 Tout d’abord, vous créez deux nouveaux sous-sites SharePoint : un pour héberger les flux de travail réutilisables à partir de SharePoint Designer, un autre pour héberger les workflows convertis.

#### <a name="to-create-sharepoint-subsites"></a>Pour créer des sous-sites SharePoint

1. Dans SharePoint Designer 2010, dans la barre de menus, choisissez **fichier**  >  **nouveau site Web vide**.

2. Dans la boîte de dialogue **nouveau site Web vide** , accédez à un site SharePoint où vous souhaitez créer le flux de travail, ou utilisez la valeur de http://<em>SystemName</em>/, puis cliquez sur le bouton **OK** .

    La page d’hébergement s’affiche.

3. Dans la section sous- **sites** , cliquez sur le bouton **nouveau** .

4. Dans la boîte de dialogue **nouveau** , choisissez **modèles SharePoint** dans la liste dans le volet gauche, puis choisissez **site d’équipe** dans la liste dans le volet droit.

5. Dans la zone **Spécifiez l’emplacement du site Web** , remplacez le mot sous- **site** dans l’URL par **SPD1**, puis cliquez sur le bouton **OK** .

    Cela ouvre le nouveau sous-site dans SharePoint Designer. Fermez cette instance de SharePoint Designer et revenez à la première instance (le site de niveau supérieur).

6. Répétez les étapes 3-5 pour créer le deuxième sous-site, en remplaçant cette fois le sous- **site** Word dans [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] par **SPD2**.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Créer un flux de travail réutilisable SharePoint Designer
 Comme SharePoint n’inclut pas de flux de travail réutilisables que vous pouvez utiliser pour cet exemple, vous allez en créer un. Dans ce flux de travail simple, lorsqu’un utilisateur entre une nouvelle tâche dans la liste des tâches qui a un titre spécifique, la tâche est affectée à cet utilisateur.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Pour créer un flux de travail réutilisable SharePoint Designer

1. Dans la section sous- **sites** , choisissez le site **SPD1** pour le modifier.

2. Sur le ruban, cliquez sur le bouton **flux de travail réutilisable** .

     L’assistant créer un flux de travail réutilisable s’affiche.

3. Dans la zone **nom** , entrez **flux de travail de la tâche SPD**.

4. Dans la liste **type de contenu** , choisissez **tâche**, puis choisissez le bouton **OK** .

     Le flux de travail s’ouvre dans le concepteur de flux de travail SharePoint Designer.

5. Dans le concepteur de flux de travail, choisissez l’étape 1, puis, dans le ruban, cliquez sur le bouton **condition** .

6. Dans la liste des conditions, choisissez **si le champ d’élément actuel est égal** à la valeur.

     Cette étape ajoute une condition nommée si le **champ est égal** à la valeur.

7. Dans la condition **si le champ est égal** à la valeur, choisissez le lien de **champ** .

8. Dans la liste des valeurs, choisissez **titre**.

9. Dans la condition **si le champ est égal** à la valeur, choisissez le lien **valeur** .

10. Dans la zone, entrez **nouvelle tâche**.

     L’instruction de condition lit maintenant **si élément actuel : le titre est égal à nouvelle tâche**.

11. Choisissez la ligne sous l’instruction de condition, puis, dans le ruban, cliquez sur le bouton **action** .

12. Dans la liste des actions, choisissez **définir le champ dans l’élément actuel**.

13. Dans l’action **définir la valeur du champ** , choisissez le lien du **champ** , puis, dans la liste, choisissez **assigné à**.

14. Dans l’action **définir la valeur du champ** , choisissez le lien **valeur** , puis, dans la liste des utilisateurs et des groupes existants, choisissez **utilisateur qui a créé l’élément**.

15. Choisissez le bouton **Ajouter** , puis choisissez le bouton **OK** .

     L’instruction action lit maintenant **définir affecté à sur élément actuel : CreatedBy**.

## <a name="save-and-deploy-the-reusable-workflow"></a>Enregistrer et déployer le flux de travail réutilisable
 Étant donné que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] peut importer uniquement des fichiers *. wsp* , vous devez enregistrer le flux de travail réutilisable sous la forme d’un fichier *. wsp* et le déployer sur SharePoint avant de l’importer dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

> [!IMPORTANT]
> Si vous recevez une erreur d’exécution lors de l’exécution de la procédure suivante, vous devez effectuer la procédure sur un système qui a accès au site SharePoint.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Pour enregistrer et déployer le flux de travail réutilisable

1. En haut de SharePoint Designer, choisissez le bouton **Enregistrer** pour enregistrer votre progression, puis cliquez sur le bouton **publier** pour déployer le flux de travail sur le site SharePoint **SPD1** .

2. Dans le volet de navigation, choisissez l’objet **flux de travail** .

3. Sous **flux de travail réutilisable**, choisissez flux de travail de la **tâche SPD**.

4. Sur le ruban, cliquez sur le bouton **Enregistrer comme modèle** pour enregistrer le flux de travail en tant que fichier *. wsp* .

5. Ouvrez le site SharePoint **SPD1** dans un navigateur pour afficher le fichier *. wsp* dans SharePoint.

6. Dans la barre de lancement rapide, choisissez le lien **bibliothèques** .

7. Dans la section **bibliothèques de documents** , choisissez le lien ressources du **site** .

     Le fichier de flux de travail de la **tâche SPD** est listé avec d’autres ressources du site.

8. Dans la liste des fichiers, sélectionnez le nom de ce fichier

9. Dans la boîte de dialogue **téléchargement de fichier** , choisissez le bouton **Enregistrer** pour enregistrer le fichier *. wsp* sur votre système local.

## <a name="import-the-wsp-file-into-visual-studio"></a>Importer le fichier. wsp dans Visual Studio
 Importez le fichier *. wsp* dans à [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] l’aide d’un projet d’importation de flux de travail réutilisable. Ce projet convertit le flux de travail à partir d’un flux de travail déclaratif et réutilisable en un flux de travail de code. Une fois le flux de travail converti, vous allez utiliser le code pour modifier son comportement.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Pour importer un workflow à partir d’un fichier. wsp et le modifier

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

2. Dans la boîte de dialogue **nouveau projet** , développez le nœud **SharePoint** sous **Visual C#** ou **Visual Basic**, puis choisissez le nœud **2010** .

3. Dans le volet **modèles** , choisissez le modèle **importer le flux de travail SharePoint 2010 réutilisable** , laissez le nom du projet **WorkflowImportProject1**, puis choisissez le bouton **OK** .

    L'Assistant Personnalisation de SharePoint apparaît.

4. Dans la page **spécifier le site et le niveau de sécurité pour le débogage** , entrez la [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] pour le deuxième sous-site SharePoint que vous avez créé précédemment : http://<em>System Name</em>/SPD2.

5. Dans la section **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez la case **d’option déployer en tant que solution de batterie** , puis cliquez sur le bouton **suivant** .

    Pour plus d’informations sur les solutions sandbox et les solutions de batterie de serveurs, consultez Considérations sur les [solutions bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md).

6. Dans la page **spécifier la nouvelle source du projet** , accédez à l’emplacement du système où vous avez enregistré le fichier *. wsp* précédemment, ouvrez le fichier, puis choisissez le bouton **suivant** .

   > [!NOTE]
   > Choisissez le bouton **Terminer** pour importer tous les éléments disponibles dans le fichier *. wsp* .

    Cela permet d’afficher la liste des flux de travail réutilisables pouvant être importés.

7. Dans la zone **Sélectionner les éléments à importer** , choisissez le flux de travail de flux de travail de **tâche SPD** , puis choisissez le bouton **Terminer** .

    Une fois l’opération d’importation terminée, un projet nommé **WorkflowImportProject1** est créé et contient un flux de travail nommé **SPD_Workflow_TestFT**. Dans ce dossier se trouve le fichier de définition du flux de travail *Elements.xml* et le fichier du concepteur de flux de travail (*. xoml*). Le concepteur contient deux fichiers : le fichier de règles (. Rules) et le fichier code-behind ( *. cs* ou *. vb*, selon le langage de programmation de votre projet).

8. Dans **Explorateur de solutions**, supprimez le dossier **autres fichiers importés** .

9. Dans le fichier *Elements.xml* , supprimez `InstantiationURL="_layouts/IniErkflIP.sspx"` .

10. Dans **Explorateur de solutions**, choisissez **WorkflowImportProject1**, puis, dans la barre de menus, choisissez **projet**  >  **définir comme projet de démarrage** pour définir **WorkflowImportProject1** comme élément de démarrage.

     La liste s’affiche immédiatement lorsque vous déboguez le projet.

11. Étant donné que le modèle de **flux de travail SharePoint 2010 d’importation réutilisable** n’importe pas les valeurs de propriété d’association pour le flux de travail importé, vous devez les entrer. Pour ce faire :

    1. Dans **Explorateur de solutions**, choisissez le nœud **SPD_Workflow_TestFT** .

    2. Cliquez sur le bouton de sélection (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")) en regard de l’une des propriétés de liste, par exemple la propriété **liste cible** .

    3. Renseignez les valeurs manquantes dans l’Assistant Personnalisation de SharePoint, puis choisissez le bouton **Terminer** .

12. Choisissez le fichier. xoml, puis, dans la barre de menus, choisissez **View**  >  **Concepteur** de vues pour afficher le flux de travail importé dans le concepteur de flux de travail.

13. Dans le nœud **Windows Workflow v 3.0** de la **boîte à outils**, effectuez l’une des opérations suivantes :

    - Ouvrez le menu contextuel de l’activité **code** , puis choisissez **copier**. Dans le concepteur de flux de travail, ouvrez le menu contextuel de la ligne sous l’activité **SequenceActivity1** , puis choisissez **coller**.

    - Faites glisser l’activité **code** de la **boîte à outils** vers le concepteur de flux de travail, puis connectez-la à la ligne sous l’activité **SequenceActivity1** .

      Cela ajoute une activité au concepteur de flux de travail nommé **CodeActivity1**. Dans cette activité, vous allez ajouter une action de code qui crée une annonce dans la liste annonces lorsque l’utilisateur démarre le flux de travail.

14. Effectuez l'un des ensembles d'étapes suivants :

    - Double-cliquez sur **CodeActivity1** pour générer un gestionnaire d’événements et afficher le code.

    - Dans la fenêtre **Propriétés** de **CodeActivity1**, définissez la valeur de la propriété **ExecuteCode** sur **codeActivity_ExecuteCode**.

15. Ajoutez le code suivant sous les directives **using** ou **Imports** existantes :

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. Remplacez `codeActivity1_ExecuteCode` par ce qui suit :

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>Déployer le projet et associer le flux de travail
 Ensuite, exécutez WorkflowImportProject1 pour le déployer sur un site SharePoint, puis associez le flux de travail à la liste des tâches pour afficher et tester le workflow modifié et converti.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Pour déployer le projet et associer le flux de travail

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , appuyez sur la touche **F5** pour exécuter et déployer le projet de workflow converti.

2. Dans la barre de lancement rapide, choisissez le lien **tâches** pour afficher la liste des tâches.

3. Dans l’onglet **outils de liste** , choisissez le bouton **éléments** , puis cliquez sur le bouton **nouvel élément** .

     La boîte de dialogue **tâches-nouvel élément** s’ouvre.

4. Dans la zone **titre** , entrez **nouvelle tâche**, puis cliquez sur le bouton **Enregistrer** .

5. Dans l’onglet **outils de liste** , cliquez sur le bouton **liste** , puis choisissez le bouton Paramètres de la **liste** .

     La page Paramètres de la **liste** s’affiche.

6. Dans la section **autorisations et gestion** , choisissez le lien **paramètres de flux de travail** .

     La page **paramètres de flux de travail** s’affiche.

7. Choisissez le lien **Ajouter un flux de travail** .

8. Dans la liste **flux de travail** , choisissez **WorkflowImportProject1-test de flux de travail SPD**.

9. Dans la zone **nom** , entrez **test de flux de travail SPD**, puis choisissez le bouton **OK** .

10. Dans la barre de lancement rapide, choisissez la liste **tâches** .

11. Cliquez sur la flèche en regard de **nouvelle tâche**, puis, dans la liste, choisissez **flux de travail**.

12. Dans la section **Démarrer un nouveau flux de travail** , choisissez le lien pour le **test de flux de travail SPD**, puis choisissez le bouton **Démarrer** pour lancer le flux de travail.

    > [!NOTE]
    > Vous pouvez également associer automatiquement un flux de travail à une liste en exécutant l’Assistant paramètres de flux de travail et en définissant le flux de travail sur auto-association.

     Notez que deux actions sont effectuées par le flux de travail : votre nom s’affiche dans la colonne **affecté à** de la tâche, et une annonce apparaît dans la liste **annonces** .

## <a name="see-also"></a>Voir aussi
- [Importer des éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)

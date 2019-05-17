---
title: 'Procédure pas à pas : Importer un flux de travail réutilisable de SharePoint Designer dans Visual Studio | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: c7d1373339fac4768e2af1eda5770d5058ae8078
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446593"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>Procédure pas à pas : Importer un flux de travail réutilisable de SharePoint Designer dans Visual Studio
  Cette procédure pas à pas montre comment importer un flux de travail réutilisable créé avec SharePoint Designer 2010 dans un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projet de flux de travail SharePoint.

 Flux de travail créés dans SharePoint Designer, ou *flux de travail déclaratifs*, se composent de [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instructions au lieu de code. SharePoint Designer 2010 introduit *flux de travail réutilisables*, qui sont portables déclarative des flux de travail qui peut être utilisé par différentes listes dans les sites SharePoint.

 Les workflows créés dans [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], tels que des flux de travail séquentiels et d’état machine, sont appelés *des flux de travail de code*. Flux de travail de code se compose de fichiers XML et les modules de code dans lequel les utilisateurs peuvent personnaliser le comportement du flux de travail.

 Visual Studio vous permet d'importer des flux de travail réutilisables créés dans SharePoint Designer 2010 et de les convertir sous forme de flux de travail avec code en vue de les exploiter sur vos sites SharePoint.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un flux de travail simple et réutilisable dans SharePoint Designer.

- Exportation du flux de travail réutilisable de SharePoint Designer pour un *.wsp* fichier et dans SharePoint.

- L’importation de la *.wsp* votre fichier en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en utilisant le projet de flux de travail réutilisable importation.

- Modification du flux de travail en ajoutant du code.

- À l’aide du flux de travail importé dans un site SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Éditions prises en charge [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] et SharePoint.

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>Créer des sous-sites de SharePoint cible
 Tout d’abord, vous créez deux nouveaux sous-sites SharePoint : un pour héberger les flux de travail réutilisable de SharePoint Designer, un autre pour héberger les flux de travail converti.

#### <a name="to-create-sharepoint-subsites"></a>Pour créer des sous-sites de SharePoint

1. Dans SharePoint Designer 2010, dans la barre de menus, choisissez **fichier** > **nouveau Site Web vide**.

2. Dans le **nouveau Site Web vide** boîte de dialogue, accédez à un site SharePoint où vous souhaitez créer le flux de travail, ou utilisez la valeur http://<em>Nom_système</em>/, puis choisissez le **OK** bouton.

    La page d’accueil s’affiche.

3. Dans le **sous-sites** , choisissez le **New** bouton.

4. Dans le **New** boîte de dialogue, sélectionnez **modèles SharePoint** à partir de la liste dans le volet gauche, puis choisissez **Site d’équipe** dans la liste dans le volet droit.

5. Dans le **spécifier l’emplacement du site Web** zone, remplacez le mot **sous-site** dans l’URL par **SPD1**, puis choisissez le **OK** bouton.

    Cette opération ouvre le nouveau sous-site dans SharePoint Designer. Fermez cette instance de SharePoint Designer, puis revenez à la première instance (site de niveau supérieur).

6. Répétez les étapes 3 à 5 pour créer le deuxième sous-site, cette fois en remplaçant le mot **sous-site** dans le [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] avec **SPD2**.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Créer un flux de travail réutilisable de SharePoint Designer
 Étant donné que SharePoint n’inclut pas de n’importe quel flux de travail réutilisables que vous pouvez utiliser pour cet exemple, vous allez créer un. Dans ce flux de travail simple, lorsqu’un utilisateur entre une nouvelle tâche dans la liste des tâches qui a un logiciel spécifique, la tâche est affectée à cet utilisateur.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Pour créer un flux de travail réutilisable de SharePoint Designer

1. Dans le **sous-sites** , choisissez le **SPD1** site pour le modifier.

2. Dans le ruban, choisissez le **flux de travail réutilisable** bouton.

     L’Assistant de créer le flux de travail réutilisable s’affiche.

3. Dans le **nom** , entrez **tâches SPD**.

4. Dans le **Type de contenu** , choisissez **tâche**, puis choisissez le **OK** bouton.

     Le flux de travail s’ouvre dans le Concepteur de flux de travail SharePoint Designer.

5. Dans le Concepteur de flux de travail, sélectionnez l’étape 1, puis, dans le ruban, choisissez le **Condition** bouton.

6. Dans la liste des conditions, choisissez **si le champ d’élément actuel est égal à la valeur**.

     Cette étape ajoute une condition qui est nommée **si le champ est égal à la valeur**.

7. Dans le **si le champ est égal à la valeur** de condition, choisissez le **champ** lien.

8. Dans la liste de valeurs, choisissez **titre**.

9. Dans le **si le champ est égal à la valeur** de condition, choisissez le **valeur** lien.

10. Dans la zone, entrez **nouvelle tâche**.

     L’instruction de condition maintenant **si en cours : titre de l’élément est égal à la nouvelle tâche**.

11. Choisissez la ligne sous l’instruction de condition, puis, dans le ruban, le **Action** bouton.

12. Dans la liste des actions, choisissez **champ de jeu dans l’élément actif**.

13. Dans le **valeur du champ de jeu** action, choisissez le **champ** lier et, dans la liste, choisissez **affectés à**.

14. Dans le **valeur du champ de jeu** action, choisissez le **valeur** lier et, dans la liste des utilisateurs et groupes existants, choisissez **utilisateur ayant créé l’élément**.

15. Choisissez le **ajouter** bouton, puis choisissez le **OK** bouton.

     L’instruction action maintenant **définir assigné à élément actif : CreatedBy**.

## <a name="save-and-deploy-the-reusable-workflow"></a>Enregistrer et déployer le flux de travail réutilisable
 Étant donné que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] peut importer uniquement *.wsp* fichiers, vous devez enregistrer le flux de travail réutilisable en tant qu’un *.wsp* de fichiers et le déployer sur SharePoint avant de les importer dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

> [!IMPORTANT]
> Si vous recevez une erreur d’exécution la procédure suivante, vous devez effectuer la procédure sur un système qui a accès au site SharePoint.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Pour enregistrer et déployer le flux de travail réutilisable

1. En haut de SharePoint Designer, choisissez le **enregistrer** bouton pour enregistrer votre progression, puis choisissez le **publier** bouton pour déployer le flux de travail pour le **SPD1** site SharePoint .

2. Dans le volet de Navigation, choisissez le **Workflows** objet.

3. Sous **flux de travail réutilisable**, choisissez **tâches SPD**.

4. Dans le ruban, choisissez le **enregistrer comme modèle** bouton pour enregistrer le flux de travail comme un *.wsp* fichier.

5. Ouvrez le **SPD1** site SharePoint dans un navigateur pour afficher le *.wsp* fichier dans SharePoint.

6. Dans la barre de lancement rapide, choisissez le **bibliothèques** lien.

7. Dans le **bibliothèques de documents** , choisissez le **les ressources de Site** lien.

     Le **tâches SPD** fichier est répertorié avec les autres ressources de site.

8. Dans la liste des fichiers, sélectionnez le nom de ce fichier

9. Dans le **téléchargement de fichier** boîte de dialogue, sélectionnez le **enregistrer** bouton pour enregistrer le *.wsp* fichier sur votre système local.

## <a name="import-the-wsp-file-into-visual-studio"></a>Importer le fichier .wsp dans Visual Studio
 Importer le *.wsp* votre fichier en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] à l’aide d’un projet de flux de travail réutilisable importation. Ce projet convertit le flux de travail à partir d’un flux de travail réutilisable déclaratif en un flux de travail de code. Une fois que le flux de travail est converti, vous utiliserez le code pour modifier son comportement.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Importer un workflow à partir d’un fichier .wsp et le modifier

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dans la barre de menus, choisissez **fichier** > **New** > **projet**.

2. Dans le **nouveau projet** boîte de dialogue, développez le **SharePoint** nœud sous **Visual C#** ou **Visual Basic**, puis choisissez le **2010** nœud.

3. Dans le **modèles** volet, choisissez le **importation de flux de travail réutilisable SharePoint 2010** modèle, laisser le nom du projet en tant que **WorkflowImportProject1**, puis choisissez le **OK** bouton.

    L’Assistant de personnalisation de SharePoint s’affiche.

4. Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, entrez le [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] du deuxième sous-site SharePoint que vous avez créé précédemment : http://<em>nom système</em>  /SPD2.

5. Dans le **quel est le niveau de confiance de cette solution SharePoint ?** , choisissez le **déployer en tant que solution de batterie** case d’option, puis choisissez le **suivant** bouton.

    Pour plus d’informations sur sandbox par rapport aux solutions de batterie de serveurs, consultez [considérations relatives à la solution bac à sable](../sharepoint/sandboxed-solution-considerations.md).

6. Dans le **spécifier la nouvelle source de projet** page, accédez à l’emplacement sur le système où vous avez enregistré le *.wsp* de fichiers, ouvrez le fichier, puis choisissez le **suivant** bouton.

   > [!NOTE]
   > Choisissez le **Terminer** bouton Importer tous les éléments disponibles dans le *.wsp* fichier.

    Cela affiche une liste de flux de travail réutilisables disponibles pour l’importation.

7. Dans le **sélectionner les éléments à importer** , sélectionnez le **tâches SPD** flux de travail, puis choisissez le **Terminer** bouton.

    Une fois l’opération d’importation est terminée, un projet nommé **WorkflowImportProject1** est créé contenant un flux de travail nommé **SPD_Workflow_TestFT**. Dans ce dossier est le fichier de définition du flux de travail *Elements.xml* et le fichier de Concepteur de flux de travail (*.xoml*). Le concepteur contient deux fichiers : le fichier de règles (.rules) et le fichier code-behind (soit *.cs* ou *.vb*, en fonction de langage de programmation de votre projet).

8. Dans **l’Explorateur de solutions**, supprimez le **autres fichiers importés** dossier.

9. Dans le *Elements.xml* , supprimez `InstantiationURL="_layouts/IniErkflIP.sspx"`.

10. Dans **l’Explorateur de solutions**, choisissez **WorkflowImportProject1**, puis, dans la barre de menus, choisissez **projet** > **définir comme projet de démarrage**  pour définir **WorkflowImportProject1** comme élément de démarrage.

     La liste s’affiche immédiatement lorsque vous déboguez le projet.

11. Étant donné que le **importer SharePoint 2010 réutilisable** modèle n’importe pas les valeurs de propriété d’association pour le flux de travail importé, vous devez les entrer. Pour ce faire :

    1. Dans **l’Explorateur de solutions**, choisissez le **SPD_Workflow_TestFT** nœud.

    2. Choisissez le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")) bouton en regard d’une des propriétés de la liste, tels que le **liste cible** propriété.

    3. Renseignez les valeurs manquantes dans l’Assistant de personnalisation de SharePoint, puis choisissez le **Terminer** bouton.

12. Choisissez le fichier .xoml, puis, dans la barre de menus, **vue** > **concepteur** pour afficher le flux de travail importé dans le Concepteur de flux de travail.

13. Dans le **Windows Workflow v3.0** nœud de la **boîte à outils**, effectuez l’une des étapes suivantes :

    - Ouvrez le menu contextuel pour le **Code** activité, puis choisissez **copie**. Dans le Concepteur de flux de travail, ouvrez le menu contextuel de la ligne sous le **SequenceActivity1** activité, puis choisissez **coller**.

    - Faites glisser le **Code** activité à partir de la **boîte à outils** vers le Concepteur de flux de travail et connectez-la à la ligne sous le **SequenceActivity1** activité.

      Cette opération ajoute une activité vers le Concepteur de flux de travail nommé **CodeActivity1**. Dans cette activité, vous allez ajouter une action de code qui crée une annonce dans la liste d’annonces lorsque l’utilisateur démarre le flux de travail.

14. Effectuez l'un des ensembles d'étapes suivants :

    - Double-cliquez sur **CodeActivity1** pour générer un gestionnaire d’événements et afficher le code.

    - Dans le **propriétés** fenêtre pour **CodeActivity1**, définissez la valeur de la **ExecuteCode** propriété **codeActivity_ExecuteCode**.

15. Ajoutez le code suivant sous existant **à l’aide de** ou **importations** instructions :

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. Remplacez `codeActivity1_ExecuteCode` par le code suivant :

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>Déployer le projet et associer le flux de travail
 Ensuite, exécutez WorkflowImportProject1 pour déployez-le sur un site SharePoint, puis associez le flux de travail à la liste des tâches pour afficher et de test modifié, converti en flux de travail.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Pour déployer le projet et associer le flux de travail

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], choisissez le **F5** clé pour exécuter et déployer le projet de flux de travail converti.

2. Dans la barre de lancement rapide, choisissez le **tâches** lien pour afficher la liste des tâches.

3. Sur le **outils de liste** , choisir le **éléments** bouton, puis choisissez le **un nouvel élément** bouton.

     Le **tâches - nouvel élément** boîte de dialogue s’ouvre.

4. Dans le **titre** , entrez **nouvelle tâche**, puis choisissez le **enregistrer** bouton.

5. Sur le **outils de liste** , choisir le **liste** bouton, puis choisissez le **liste paramètres** bouton.

     Le **liste paramètres** page s’affiche.

6. Dans le **autorisations et gestion** , choisissez le **les paramètres de flux de travail** lien.

     Le **les paramètres de flux de travail** page s’affiche.

7. Choisissez le **ajouter un flux de travail** lien.

8. Dans le **Workflow** , choisissez **WorkflowImportProject1 - Test du flux de travail SPD**.

9. Dans le **nom** , entrez **Test du flux de travail SPD**, puis choisissez le **OK** bouton.

10. Dans la barre de lancement rapide, choisissez le **tâches** liste.

11. Cliquez sur la flèche à côté **nouvelle tâche**, puis, dans la liste, choisissez **des flux de travail**.

12. Dans le **démarrer un nouveau Workflow** , choisissez le lien pour **Test du flux de travail SPD**, puis choisissez le **Démarrer** bouton pour lancer le flux de travail.

    > [!NOTE]
    > Ou bien, vous pouvez associer automatiquement un flux de travail avec une liste en exécutant l’Assistant paramètres de flux de travail et en définissant le flux de travail pour associer automatiquement.

     Notez que les deux actions sont effectuées par le flux de travail : votre nom s’affiche dans la tâche **assigné à** colonne et une annonce s’affiche dans le **annonces** liste.

## <a name="see-also"></a>Voir aussi
- [Importer des éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Créer des contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)

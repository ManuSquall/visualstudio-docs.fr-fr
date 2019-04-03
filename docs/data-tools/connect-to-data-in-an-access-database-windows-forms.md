---
title: Se connecter à des données dans une base de données Access (Windows Forms)
ms.date: 02/12/2019
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9d4fcce4664483cd1d981f6a0b1233a6302c553b
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647347"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Se connecter à des données dans une base de données Access (Windows Forms)

Vous pouvez vous connecter à une base de données Access (soit un *.mdf* fichier ou un *.accdb* fichier) à l’aide de Visual Studio. Après avoir défini la connexion, les données s’affichent dans la fenêtre **Sources de données**. De là, vous pouvez faire glisser des tables ou des vues sur vos formulaires.

## <a name="prerequisites"></a>Prérequis

Pour utiliser ces procédures, vous avez besoin d’un projet Application Windows Forms et d’une base de données Access (fichier *.accdb*) ou d’une base de données Access 2000-2003 (fichier *.mdb*). Suivez la procédure qui correspond à votre type de fichier.

## <a name="create-a-dataset-for-an-accdb-file"></a>Créer un jeu de données pour un fichier .accdb

Vous pouvez vous connecter aux bases de données créés via Access 2013, Office 365, Access 2010 ou Access 2007 à l’aide de la procédure suivante.

1. Ouvrez l’application Windows Forms à laquelle vous voulez connecter des données.

2. Pour ouvrir le **des Sources de données** fenêtre, dans le **vue** menu, sélectionnez **Windows autres** > **des Sources de données**.

   ![Afficher d'autres sources de données Windows](../data-tools/media/viewdatasources.png)

3. Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

   L’Assistant **Configuration de source de données** s’ouvre.

4. Sélectionnez **base de données** sur le **choisir un Type de Source de données** page, puis sélectionnez **suivant**.

5. Sélectionnez **Dataset** sur le **choisir un modèle de base de données** page, puis sélectionnez **suivant**.

6. Dans la page **Choisir votre connexion de données**, sélectionnez **Nouvelle connexion** pour configurer une nouvelle connexion de données.

   La boîte de dialogue **Ajouter une connexion** s’ouvre.

7. Si **source de données** n’a pas la valeur **du fichier de base de données Microsoft Access (OLE DB)**, sélectionnez le **modification** bouton.

   Le **modifier la Source de données** boîte de dialogue s’ouvre. Dans la liste des sources de données, choisissez **fichier de base de données Microsoft Access**. Dans le **fournisseur de données** liste déroulante, sélectionnez **fournisseur de données .NET Framework pour OLE DB**, puis choisissez **OK**.

8. Choisissez **Parcourir** regard **nom de fichier de base de données**, puis accédez à votre *.accdb* de fichier et choisissez **Open**.

9. Entrez un nom d’utilisateur et le mot de passe (si nécessaire), puis choisissez **OK**.

10. Sélectionnez **suivant** sur le **choisir votre connexion de données** page.

     Vous pouvez obtenir une boîte de dialogue qui vous indique que le fichier de données n’est pas dans votre projet actuel. Sélectionnez **Oui** ou **Non**.

11. Sélectionnez **suivant** sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** page.

12. Développez le nœud **Tables** dans la page **Choisir vos objets de base de données**.

13. Sélectionnez les tables ou vues que vous souhaitez inclure dans votre jeu de données, puis sélectionnez **Terminer**.

     Le jeu de données est ajouté à votre projet, et les tables et vues s’affichent dans la fenêtre **Sources de données**.

## <a name="create-a-dataset-for-an-mdb-file"></a>Créer un jeu de données pour un fichier .mdb

Pour créer le jeu de données, exécutez l’**Assistant Configuration de source de données**.

1. Ouvrez l’application Windows Forms à laquelle vous voulez connecter des données.

2. Sur le **vue** menu, sélectionnez **Windows autres** > **des Sources de données**.

   ![Afficher d'autres sources de données Windows](../data-tools/media/viewdatasources.png)

3. Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

    L’Assistant **Configuration de source de données** s’ouvre.

4. Sélectionnez **base de données** sur le **choisir un Type de Source de données** page, puis sélectionnez **suivant**.

5. Sélectionnez **Dataset** sur le **choisir un modèle de base de données** page, puis sélectionnez **suivant**.

6. Dans la page **Choisir votre connexion de données**, sélectionnez **Nouvelle connexion** pour configurer une nouvelle connexion de données.

7. Si la source de données n’est pas **du fichier de base de données Microsoft Access (OLE DB)**, sélectionnez **modification** pour ouvrir le **modifier la Source de données** boîte de dialogue et sélectionnez **Microsoft Accéder au fichier de base de données**, puis sélectionnez **OK**.

8. Dans le **nom de fichier de base de données**, spécifiez le chemin d’accès et le nom de la *.mdb* fichier que vous souhaitez vous connecter à, puis sélectionnez **OK**.

   ![Ajouter une connexion à un fichier de base de données Access](../data-tools/media/add-connection-access-db.png)

9. Sélectionnez **suivant** sur le **choisir votre connexion de données** page.

10. Sélectionnez **suivant** sur le **enregistrer la chaîne de connexion dans le fichier de Configuration de l’Application** page.

11. Développez le nœud **Tables** dans la page **Choisir vos objets de base de données**.

12. Sélectionnez les tables ou des vues de votre choix dans votre jeu de données, puis sélectionnez **Terminer**.

    Le jeu de données est ajouté à votre projet, et les tables et vues s’affichent dans la fenêtre **Sources de données**.

## <a name="security"></a>Sécurité

Le stockage d'informations sensibles (telles qu'un mot de passe) peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="next-steps"></a>Étapes suivantes

Le jeu de données que vous venez de créer est maintenant disponible dans le **des Sources de données** fenêtre. Vous pouvez à présent effectuer l’une des tâches suivantes :

- Sélectionnez des éléments dans le **des Sources de données** fenêtre et faites-les glisser jusqu'à votre formulaire (voir [lier les formulaires Windows contrôle aux données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Ouvrez la source de données dans le **Concepteur de DataSet** pour ajouter ou modifier les objets qui composent le jeu de données.

- Ajouter une logique de validation pour le <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> événement les tables de données dans le jeu de données (voir [valider des données dans les jeux de données](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Voir aussi

- [Ajouter des connexions](../data-tools/add-new-connections.md)
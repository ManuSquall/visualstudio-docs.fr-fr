---
title: Mettre à jour des fichiers .mdf
description: Passez en revue les options de mise à niveau d’un fichier de base de données (. mdf) après avoir installé une version plus récente de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: babc82469d32540f1a003b629c9d83887ca91595
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998042"
---
# <a name="upgrade-mdf-files"></a>Mettre à jour des fichiers .mdf

Cette rubrique décrit les options de mise à niveau d’un fichier de base de données (*. mdf*) après l’installation d’une version plus récente de Visual Studio. Il comprend des instructions pour les tâches suivantes :

- Mettre à niveau un fichier de base de données pour utiliser une version plus récente de SQL Server Express base de données locale

- Mettre à niveau un fichier de base de données pour utiliser une version plus récente de SQL Server Express

- Utiliser un fichier de base de données dans Visual Studio, mais conserver la compatibilité avec une version antérieure de SQL Server Express ou de base de données locale

- Rendre SQL Server Express le moteur de base de données par défaut

Vous pouvez utiliser Visual Studio pour ouvrir un projet qui contient un fichier de base de données (*. mdf*) qui a été créé à l’aide d’une version antérieure de SQL Server Express ou de la base de données locale. Toutefois, pour continuer à développer votre projet dans Visual Studio, vous devez disposer de cette version de SQL Server Express ou de la base de données locale installée sur le même ordinateur que Visual Studio, ou vous devez mettre à niveau le fichier de base de données. Si vous mettez à niveau le fichier de base de données, vous ne pourrez pas y accéder à l’aide de versions antérieures de SQL Server Express ou de base de données locale.

Vous pouvez également être invité à mettre à niveau un fichier de base de données qui a été créé à l’aide d’une version antérieure de SQL Server Express ou de la base de données locale si la version du fichier n’est pas compatible avec l’instance de SQL Server Express ou de base de données locale actuellement installée. Pour résoudre le problème, Visual Studio vous invite à mettre à niveau le fichier.

> [!IMPORTANT]
> Nous vous recommandons de sauvegarder le fichier de base de données avant de le mettre à niveau.

> [!WARNING]
> Si vous mettez à niveau un fichier *. mdf* créé dans la base de données locale 2014 (V12) 32 bits vers la base de données locale 2016 (v13) ou une version ultérieure, vous ne pourrez pas ouvrir à nouveau le fichier dans la version 32 bits de la base de données locale.

Avant de mettre à niveau une base de données, tenez compte des critères suivants :

- Ne procédez pas à la mise à niveau si vous souhaitez travailler sur votre projet dans une version antérieure et une version plus récente de Visual Studio.

- Ne procédez pas à la mise à niveau si votre application est utilisée dans les environnements qui utilisent SQL Server Express plutôt que la base de données locale.

- N’effectuez pas la mise à niveau si votre application utilise des connexions à distance, car la base de données locale ne les accepte pas.

- Ne procédez pas à la mise à niveau si votre application s’appuie sur Internet Information Services (IIS).

- Envisagez la mise à niveau si vous souhaitez tester des applications de base de données dans un environnement sandbox, mais ne souhaitez pas administrer une base de données.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Pour mettre à niveau un fichier de base de données pour utiliser la version de base de données locale

1. Dans **Explorateur de serveurs**, sélectionnez le bouton **se connecter à la base de données** .

2. Dans la boîte de dialogue **Ajouter une connexion** , spécifiez les informations suivantes :

    - **Source de données**: `Microsoft SQL Server (SqlClient)`

    - **Nom du serveur** :

        - Pour utiliser la version par défaut : `(localdb)\MSSQLLocalDB` .  Cela permet de spécifier ProjectV12 ou ProjectV13, selon la version de Visual Studio installée et la première instance de base de données locale créée. Le nœud **MSSQLLocalDB** dans **Explorateur d’objets SQL Server** indique la version vers laquelle il pointe.

        - Pour utiliser une version spécifique : `(localdb)\ProjectsV12` ou, où V12 est la base de données locale 2014 et v13 est la base de données locale `(localdb)\ProjectsV13` 2016.

    - **Attacher un fichier de base de données**: chemin d’accès physique du fichier *. mdf* principal.

    - **Nom logique**: le nom que vous souhaitez utiliser avec le fichier.

3. Cliquez sur le bouton **OK**.

4. Lorsque vous y êtes invité, sélectionnez le bouton **Oui** pour mettre à niveau le fichier.

    La base de données est mise à niveau, est attachée au moteur de base de données de base de données locale et n’est plus compatible avec la version antérieure de la base de données locale.

Vous pouvez également modifier une connexion SQL Server Express pour utiliser la base de données locale en ouvrant le menu contextuel de la connexion, puis en sélectionnant **modifier la connexion**. Dans la boîte de dialogue **modifier la connexion** , remplacez le nom du serveur par `(LocalDB)\MSSQLLocalDB` . Dans la boîte de dialogue **Propriétés avancées** , assurez-vous que l' **instance utilisateur** est définie sur **false**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Pour mettre à niveau un fichier de base de données pour utiliser la version SQL Server Express

1. Dans le menu contextuel de la connexion à la base de données, sélectionnez **modifier la connexion**.

2. Dans la boîte de dialogue **modifier la connexion** , sélectionnez le bouton **avancé** .

3. Dans la boîte de dialogue **Propriétés avancées** , sélectionnez le bouton **OK** sans modifier le nom du serveur.

    Le fichier de base de données est mis à niveau pour correspondre à la version actuelle de SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Pour utiliser la base de données dans Visual Studio, mais conserver la compatibilité avec SQL Server Express

- Dans Visual Studio, ouvrez le projet sans le mettre à niveau.

  - Pour exécuter le projet, sélectionnez la touche **F5** .

  - Pour modifier la base de données, ouvrez le fichier *. mdf* dans **Explorateur de solutions**, puis développez le nœud dans **Explorateur de serveurs** pour travailler avec votre base de données.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Pour rendre SQL Server Express le moteur de base de données par défaut

1. Dans la barre de menus, sélectionnez **Outils** > **Options**.

2. Dans la boîte de dialogue **options** , développez les options **outils de base de données** , puis sélectionnez **connexions de données**.

3. Dans la zone de texte nom de l' **instance SQL Server** , spécifiez le nom de l’instance de SQL Server Express ou de la base de données locale que vous souhaitez utiliser. Si l’instance n’est pas nommée, spécifiez `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB` .

4. Cliquez sur le bouton **OK**.

    SQL Server Express sera le moteur de base de données par défaut pour vos applications.

## <a name="see-also"></a>Voir aussi

- [Accès aux données dans Visual Studio](accessing-data-in-visual-studio.md)

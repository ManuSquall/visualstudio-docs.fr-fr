---
title: Outils de données Visual Studio pour C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: a853edf80cd11400b2e54c17dfe95f1ccfb1c822
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-data-tools-for-c"></a>Outils de données Visual Studio pour C++

C++ natif peut souvent fournissent de meilleures performances lorsque vous accédez à des sources de données. Toutefois, les données des outils pour les applications C++ dans Visual Studio ne sont pas aussi riches car il s’agit des applications .NET. Par exemple, les fenêtres sources de données ne peut pas servir de glisser et déposer des sources de données sur une aire de conception de C++. Si vous avez besoin d’une couche objet-relationnel, vous devez écrire votre propre, ou utiliser un produit tiers.  Est de même pour les fonctionnalités de liaison de données, bien que les applications qui utilisent la bibliothèque Microsoft Foundation Class peuvent utiliser certaines classes de base de données, ainsi que des documents et des vues, pour stocker les données en mémoire et l’afficher à l’utilisateur. Pour plus d’informations, consultez [accès aux données dans Visual C++](/cpp/data/data-access-in-cpp).

Pour vous connecter aux bases de données SQL, les applications C++ natives peuvent utiliser les pilotes ODBC et OLE DB et le fournisseur ADO qui sont inclus avec Windows. Ceux-ci peuvent se connecter aux bases de données qui prend en charge ces interfaces. Le pilote ODBC est la norme. OLE DB est fourni pour la compatibilité descendante. Pour plus d’informations sur ces technologies de données, consultez [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814.aspx).

Pour tirer parti des fonctionnalités personnalisées dans SQL Server 2005 et version ultérieure, utilisez le [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Le client natif contient également le pilote ODBC de SQL Server et le fournisseur OLE DB pour SQL Server dans une bibliothèque de liens dynamiques (DLL). Ils prennent en charge des applications à l’aide des API en code natif (ODBC, OLE DB et ADO) pour Microsoft SQL Server.  SQL Server Native Client est installé avec SQL Server Data Tools. Le guide de programmation est ici : [SQL Server Native Client Programming](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Se connecter à la base de données locale via ODBC et SQL Native Client à partir d’une application C++  
  
1.  Installer SQL Server Data Tools.  
  
2.  Si vous avez besoin d’une base de données exemple SQL pour se connecter à, téléchargez la base de données Northwind et décompressez-le vers un nouvel emplacement.  
  
3.  Utilisez SQL Server Management Studio pour attacher le fichier Northwind.mdf décompressé à la base de données locale. Démarrage de SQL Server Management Studio, connectez-vous à (localdb) \MSSQLLocalDB.  
  
     ![Boîte de dialogue de connexion de SSMS](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS boîte de dialogue de connexion")  
  
     Avec le bouton droit sur le nœud de base de données locale dans le volet gauche, puis choisissez **attacher**.  
  
     ![SSMS attacher la base de données](../data-tools/media/raddata-ssms-attach-database.png "raddata SSMS attacher le base de données")  
  
4.  Téléchargez l’exemple de kit de développement logiciel Windows ODBC et décompressez-le vers un nouvel emplacement. Cet exemple montre les commandes ODBC de base qui sont utilisés pour se connecter à une base de données et les commandes et émettre des requêtes. Plus d’informations sur ces fonctions dans le [Microsoft ODBC Open Database Connectivity ()](/sql/odbc/microsoft-open-database-connectivity-odbc). Lorsque vous chargez tout d’abord la solution (il se trouve dans le dossier C++), Visual Studio propose de mise à niveau de la solution vers la version actuelle de Visual Studio. Cliquez sur **Oui**.
  
5.  Pour utiliser le client natif, vous avez besoin de son fichier d’en-tête et le fichier lib. Ces fichiers contiennent des fonctions et des définitions spécifiques de SQL Server, au-delà des fonctions ODBC définies dans sql.h. Dans **projet** > **propriétés** > **répertoires VC ++**, ajouter le répertoire include de ce qui suit :

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

Et ce répertoire de la bibliothèque :

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6.  Ajoutez ces lignes dans odbcsql.cpp. Le #define empêche pas d’importance définitions OLE DB qui est compilé.  
  
    ```cpp
    #define _SQLNCLI_ODBC_  
    #include <sqlncli.h>  
    ```  
  
    Notez que l’exemple ne pas réellement utilise toute fonctionnalité native client, les étapes précédentes ne sont pas nécessaires pour compiler et exécuter. Mais le projet est maintenant configuré pour pouvoir utiliser cette fonctionnalité. Pour plus d’informations, consultez [SQL Server Native Client Programming](/sql/relational-databases/native-client/sql-server-native-client).  
  
7.  Spécifiez le pilote à utiliser dans le sous-système ODBC. L’exemple passe l’attribut de chaîne de connexion de pilote dans comme argument de ligne de commande. Dans **projet** > **propriétés** > **débogage**, ajoutez l’argument de commande :  
  
    ```cpp
    DRIVER="SQL Server Native Client 11.0"  
    ```  
  
8.  Appuyez sur F5 pour générer et exécuter l'application. Vous devez voir une boîte de dialogue à partir du pilote qui vous invite à entrer une base de données. Entrez `(localdb)\MSSQLLocalDB`et vérifiez **utiliser une connexion approuvée**. Press **OK**. Vous devez voir une console avec les messages qui indiquent une connexion réussie. Vous devez également voir une invite de commandes où vous pouvez taper une instruction SQL. L’écran suivant montre un exemple de requête et les résultats :  
  
     ![Résultat de la requête ODBC Sample](../data-tools/media/raddata-odbc-sample-query-output.png "raddata sortie de la requête ODBC Sample")  
  
## <a name="see-also"></a>Voir aussi

[Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
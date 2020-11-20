---
title: Outils de données pour C++
description: Explorez Visual Studio Data Tools pour C++. Connectez-vous à la base de données locale via ODBC et SQL Native Client à partir d’une application C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- CPP
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 36b1fe83cb20aee6d6fc95984a254c9ac9d212bd
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998094"
---
# <a name="visual-studio-data-tools-for-c"></a>Outils de données Visual Studio pour C++

Le C++ natif peut souvent fournir des performances plus rapides lorsque vous accédez à des sources de données. Toutefois, les outils de données pour les applications C++ dans Visual Studio ne sont pas aussi riches que pour les applications .NET. Par exemple, la fenêtre **sources de données** ne peut pas être utilisée pour faire glisser et déposer des sources de données sur une aire de conception C++. Si vous avez besoin d’une couche relationnelle objet, vous devrez écrire votre propre produit ou utiliser un produit tiers. Il en va de même pour les fonctionnalités de liaison de données, bien que les applications qui utilisent la bibliothèque MFC (Microsoft Foundation Class) puissent utiliser des classes de base de données, ainsi que des documents et des vues, pour stocker des données en mémoire et les afficher à l’utilisateur. Pour plus d’informations, consultez [accès aux données dans Visual C++](/cpp/data/data-access-in-cpp).

Pour vous connecter aux bases de données SQL, les applications C++ natives peuvent utiliser les pilotes ODBC et OLE DB et le fournisseur ADO inclus avec Windows. Ils peuvent se connecter à n’importe quelle base de données qui prend en charge ces interfaces. Le pilote ODBC est la norme. OLE DB est fourni pour la compatibilité descendante. Pour plus d’informations sur ces technologies de données, consultez [composants d’accès aux données Windows](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Pour tirer parti des fonctionnalités personnalisées de SQL Server 2005 et versions ultérieures, utilisez le [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Native Client contient également l’SQL Server pilote ODBC et le fournisseur de OLE DB SQL Server dans une bibliothèque de liens dynamiques (DLL) native. Ces applications de prise en charge utilisant des API en code natif (ODBC, OLE DB et ADO) pour Microsoft SQL Server. SQL Server Native Client s’installe avec SQL Server Data Tools. Le Guide de programmation est ici : [SQL Server la programmation native client](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Pour vous connecter à la base de données locale via ODBC et SQL Native Client à partir d’une application C++

1. Installez SQL Server Data Tools.

2. Si vous avez besoin d’un exemple de base de données SQL pour vous connecter à, téléchargez la base de données Northwind et décompressez-la vers un nouvel emplacement.

3. Utilisez SQL Server Management Studio pour attacher le fichier *Northwind. mdf* décompressé à la base de données locale. Au démarrage de SQL Server Management Studio, connectez-vous à (base de données locale) \MSSQLLocalDB.

   ![Boîte de dialogue de connexion SSMS](../data-tools/media/raddata-ssms-connect-dialog.png)

   Cliquez ensuite avec le bouton droit sur le nœud de base de données locale dans le volet gauche, puis choisissez **attacher**.

   ![Base de données de SSMS Attach](../data-tools/media/raddata-ssms-attach-database.png)

4. Téléchargez l’exemple de SDK Windows ODBC et décompressez-le vers un nouvel emplacement. Cet exemple montre les commandes ODBC de base qui permettent de se connecter à une base de données et d’émettre des requêtes et des commandes. Vous pouvez en savoir plus sur ces fonctions dans le [Open Database Connectivity Microsoft (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Lorsque vous chargez la solution pour la première fois (dans le dossier C++), Visual Studio vous propose de mettre à niveau la solution vers la version actuelle de Visual Studio. Cliquez sur **Oui**.

5. Pour utiliser Native Client, vous avez besoin de son fichier d' *en-tête* et de son fichier *lib* . Ces fichiers contiennent des fonctions et des définitions spécifiques à SQL Server, au-delà des fonctions ODBC définies dans SQL. h. Dans Propriétés du **projet**  >  **Properties**  >  ,**Répertoires VC + +**, ajoutez le répertoire include suivant :

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   Et le répertoire de la bibliothèque :

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Ajoutez ces lignes dans *ODBCSQL. cpp*. Le #define empêche la compilation des définitions de OLE DB non pertinentes.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Notez que l’exemple n’utilise pas réellement les fonctionnalités Native Client, donc les étapes précédentes ne sont pas nécessaires pour la compilation et l’exécution. Mais le projet est maintenant configuré pour que vous utilisiez cette fonctionnalité. Pour plus d’informations, consultez [SQL Server Native Client programmation](/sql/relational-databases/native-client/sql-server-native-client).

7. Spécifiez le pilote à utiliser dans le sous-système ODBC. L’exemple passe l’attribut de chaîne de connexion du pilote dans en tant qu’argument de ligne de commande. Dans **Project**  >  **Properties**  >  le **débogage** des propriétés du projet, ajoutez cet argument de commande :

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Appuyez sur **F5** pour générer et exécuter l’application. Vous devez voir une boîte de dialogue du pilote qui vous invite à entrer une base de données. Entrez `(localdb)\MSSQLLocalDB` , puis cochez la case **utiliser une connexion approuvée**. Appuyez sur **OK**. Vous devez voir une console contenant des messages indiquant une connexion réussie. Vous devez également voir une invite de commandes dans laquelle vous pouvez taper une instruction SQL. L’écran suivant montre un exemple de requête et les résultats :

   ![Exemple de sortie de requête ODBC](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Voir aussi

- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

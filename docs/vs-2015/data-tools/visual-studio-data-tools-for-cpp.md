---
title: Outils de données Visual Studio C++ pour | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: ec68d54ced85737d66c64ca2dbf7942ca81e5314
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72621208"
---
# <a name="visual-studio-data-tools-for-c"></a>Outils de données Visual Studio pour C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Native C++ peut souvent fournir des performances plus rapides lorsque vous accédez à des sources de données. Toutefois, les outils de données C++ pour les applications dans Visual Studio ne sont pas aussi riches que pour les applications .net. Par exemple, les fenêtres de sources de données ne peuvent pas être utilisées pour faire glisser et C++ déposer des sources de données sur une aire de conception. Si vous avez besoin d’une couche relationnelle objet, vous devrez écrire votre propre produit ou utiliser un produit tiers.  Il en va de même pour les fonctionnalités de liaison de données, bien que les applications qui utilisent la bibliothèque MFC (Microsoft Foundation Class) puissent utiliser des classes de base de données, ainsi que des documents et des vues, pour stocker des données en mémoire et les afficher à l’utilisateur. Pour plus d’informations, consultez [accès aux données C++ dans Visual](https://msdn.microsoft.com/library/7wtdsdkh.aspx) .

 Pour se connecter aux bases de données SQL C++ , les applications natives peuvent utiliser les pilotes ODBC et OLE DB et le fournisseur ADO inclus avec Windows.     Ils peuvent se connecter à n’importe quelle base de données qui prend en charge ces interfaces. Le pilote ODBC est la norme. OLE DB est fourni pour la compatibilité descendante. Pour plus d’informations sur ces technologies de données, consultez [composants d’accès aux données Windows](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx) .

 Pour tirer parti des fonctionnalités personnalisées de SQL Server 2005 et versions ultérieures, utilisez l' [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733). Native Client contient également l’SQL Server pilote ODBC et le fournisseur de OLE DB SQL Server dans une bibliothèque de liens dynamiques (DLL) native. Ces applications de prise en charge utilisant des API en code natif (ODBC, OLE DB et ADO) pour Microsoft SQL Server.  SQL Server Native Client s’installe avec SQL Server Data Tools. Le Guide de programmation est ici : [SQL Server Native Client la programmation](https://msdn.microsoft.com/library/ms130892.aspx).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Pour vous connecter à la base de données locale via C++ ODBC et SQL Native Client à partir d’une application

1. Installez SQL Server Data Tools.

2. Si vous avez besoin d’un exemple de base de données SQL pour vous connecter à, téléchargez la base de données Northwind et décompressez-la vers un nouvel emplacement.

3. Utilisez SQL Server Management Studio pour attacher le fichier Northwind. mdf décompressé à la base de données locale. Au démarrage de SQL Server Management Studio, connectez-vous à (base de données locale) \MSSQLLocalDB.

    ![Boîte de dialogue de connexion SSMS](../data-tools/media/raddata-ssms-connect-dialog.png "boîte de dialogue raddata SSMS Connect")

    Cliquez ensuite avec le bouton droit sur le nœud de base de données locale dans le volet gauche, puis choisissez **attacher**.

    ![Base de données de SSMS Attach](../data-tools/media/raddata-ssms-attach-database.png "base de données raddata SSMS Attach")

4. Téléchargez l’exemple de SDK Windows ODBC et décompressez-le vers un nouvel emplacement. Cet exemple montre les commandes ODBC de base qui permettent de se connecter à une base de données et d’émettre des requêtes et des commandes. Vous pouvez en savoir plus sur ces fonctions dans le [Open Database Connectivity Microsoft (ODBC)](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx). Lorsque vous chargez la solution pour la première fois ( C++ dans le dossier), Visual Studio vous propose de mettre à niveau la solution vers la version actuelle de Visual Studio. Cliquez sur **Oui**.

5. Pour utiliser Native Client, vous avez besoin de son fichier d’en-tête et de son fichier lib. Ces fichiers contiennent des fonctions et des définitions spécifiques à SQL Server, au-delà des fonctions ODBC définies dans SQL. h. Dans **Project**  > **Propriétés**  > **Répertoires VC + +** , ajoutez le répertoire include suivant :

   **lecteur \<system >: \Program Files\Microsoft SQL Server\110\SDK\Include**     Et le répertoire de la bibliothèque :

   **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**

6. Ajoutez ces lignes dans ODBCSQL. cpp. Le #define empêche la compilation des définitions de OLE DB non pertinentes.

   ```
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Notez que l’exemple n’utilise pas réellement les fonctionnalités Native Client, donc les étapes précédentes ne sont pas nécessaires pour la compilation et l’exécution. Mais le projet est maintenant configuré pour que vous utilisiez cette fonctionnalité. Pour plus d’informations, consultez [SQL Server Native Client programmation](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx).

7. Spécifiez le pilote à utiliser dans le sous-système ODBC. L’exemple passe l’attribut de chaîne de connexion du pilote dans en tant qu’argument de ligne de commande. Dans **Project**  > **Propriétés**  >  le**débogage**, ajoutez cet argument de commande :

   ```
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Appuyez sur F5 pour générer et exécuter l'application. Vous devez voir une boîte de dialogue du pilote qui vous invite à entrer une base de données. Entrez `(localdb)\MSSQLLocalDB`, puis activez la case à cocher **utiliser une connexion approuvée**. Cliquez sur **OK**. Vous devez voir une console contenant des messages indiquant une connexion réussie. Vous devez également voir une invite de commandes dans laquelle vous pouvez taper une instruction SQL. L’écran suivant montre un exemple de requête et les résultats :

    ![Exemple de sortie de requête ODBC](../data-tools/media/raddata-odbc-sample-query-output.png "Exemple de sortie de requête ODBC raddata")

## <a name="see-also"></a>Voir aussi
 [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

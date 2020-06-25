---
title: 'Comment : enregistrer et modifier des chaînes de connexion'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e3cb3f832f308edb42967d2fe4485b3d6885022a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282018"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Guide pratique pour enregistrer et modifier des chaînes de connexion
Les chaînes de connexion dans les applications Visual Studio sont enregistrées dans le fichier de configuration de l’application (également appelé paramètres d’application) ou codées en dur directement dans votre application. L'enregistrement des chaînes de connexion dans le fichier de configuration de l'application simplifie la gestion de votre application. Si la chaîne de connexion doit être modifiée, vous pouvez la mettre à jour dans le fichier de paramètres de l’application (au lieu de la modifier dans le code source et de recompiler l’application).

Le stockage d'informations sensibles (telles que le mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. Les chaînes de connexion enregistrées dans le fichier de configuration de l'application ne sont pas chiffrées ou obscurcies, il est donc possible pour quiconque d'accéder au fichier et d'afficher son contenu. Le recours à la sécurité intégrée de Windows est un moyen plus sûr de contrôler l'accès à une base de données.

Si vous choisissez de ne pas utiliser la sécurité intégrée de Windows et que votre base de données requiert un nom d'utilisateur et un mot de passe, vous pouvez l'omettre dans la chaîne de connexion, mais votre application devra fournir ces informations pour pouvoir se connecter à la base de données. Par exemple, vous pouvez créer une boîte de dialogue qui invite l'utilisateur à fournir ces informations et génère dynamiquement la chaîne de connexion au moment de l'exécution. La sécurité peut encore être compromise si les informations sont interceptées sur le trajet vers la base de données.
Pour plus d’informations, consultez [protection des informations de connexion](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Pour enregistrer une chaîne de connexion à partir de l’Assistant Configuration de source de données
Dans l **'Assistant Configuration de source de données**, sélectionnez l’option permettant d’enregistrer la connexion dans la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** .

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Pour enregistrer une chaîne de connexion directement dans les paramètres de l'application
1. Dans l’**Explorateur de solutions**, double-cliquez sur l’icône **Mon projet** (Visual Basic) ou **Propriétés** (C#) pour ouvrir le **Concepteur de projets**.
1. Sélectionnez l’onglet **Paramètres**.
1. Entrez un **Nom** pour la chaîne de connexion. Faites référence à ce nom quand vous accédez à la chaîne de connexion dans le code.
1. Définissez le **Type** sur **(Chaîne de connexion)**.
1. Laissez la **Portée** définie sur **Application**.
1. Tapez votre chaîne de connexion dans le champ **valeur** ou cliquez sur le bouton des **points de suspension** (...) dans le champ **valeur** pour ouvrir la boîte de dialogue **Propriétés de connexion** et créer votre chaîne de connexion.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Modifier les chaînes de connexion stockées dans les paramètres d’application
Vous pouvez modifier les informations de connexion enregistrées dans les paramètres de l’application à l’aide du **Concepteur de projets**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Pour modifier une chaîne de connexion stockée dans les paramètres de l'application
1. Dans l’**Explorateur de solutions**, double-cliquez sur l’icône **Mon projet** (Visual Basic) ou **Propriétés** (C#) pour ouvrir le **Concepteur de projets**.
1. Sélectionnez l’onglet **Paramètres**.
1. Localisez la connexion que vous souhaitez modifier et sélectionnez le texte dans le champ **valeur** .
1. Modifiez la chaîne de connexion dans le champ **valeur** ou cliquez sur le bouton des **points de suspension** (...) dans le champ **valeur** pour modifier votre connexion à l’aide de la boîte de dialogue **Propriétés de connexion** .

## <a name="edit-connection-strings-for-datasets"></a>Modifier les chaînes de connexion pour les jeux de données
Vous pouvez modifier les informations de connexion pour chaque TableAdapter d’un jeu de données.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Pour modifier une chaîne de connexion pour un TableAdapter dans un DataSet
1. Dans **Explorateur de solutions**, double-cliquez sur le jeu de données (fichier **. xsd** ) qui contient la connexion que vous souhaitez modifier.
1. Sélectionnez le **TableAdapter** ou la requête qui possède la connexion que vous souhaitez modifier.
1. Dans la fenêtre **Propriétés** , développez le **nœud connexion**.
1. Pour modifier rapidement la chaîne de connexion, modifiez la propriété **ConnectionString** ou cliquez sur la flèche orientée vers le bas de la propriété de **connexion** , puis choisissez **nouvelle connexion**.

## <a name="security"></a>Sécurité
Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. Le recours à la sécurité intégrée de Windows est un moyen plus sûr de contrôler l'accès à une base de données.
Pour plus d’informations, consultez [protection des informations de connexion](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Voir aussi

- [Ajout de connexions](../data-tools/add-new-connections.md)

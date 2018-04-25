---
title: 'Comment : enregistrer et modifier des chaînes de connexion'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 820808a79c8ed18c08c6c54ba416c0993aac06d5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-save-and-edit-connection-strings"></a>Comment : enregistrer et modifier des chaînes de connexion
Chaînes de connexion dans les applications Visual Studio peuvent être enregistrés dans le fichier de configuration d’application (également appelé paramètres d’application) ou codées en dur directement dans votre application. L’enregistrement des chaînes de connexion dans le fichier de configuration de l’application simplifie la gestion de votre application. Si la chaîne de connexion doit être modifiée, vous pouvez la mettre à jour dans le fichier de paramètres de l'application (au lieu de la modifier dans le code source et de recompiler l'application).

Le stockage d'informations sensibles (telles que le mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. Les chaînes de connexion enregistrées dans le fichier de configuration de l'application ne sont pas chiffrées ou obscurcies, il est donc possible pour quiconque d'accéder au fichier et d'afficher son contenu. Le recours à la sécurité intégrée de Windows est un moyen plus sûr de contrôler l'accès à une base de données.

Si vous choisissez de ne pas utiliser la sécurité intégrée de Windows et que votre base de données requiert un nom d'utilisateur et un mot de passe, vous pouvez l'omettre dans la chaîne de connexion, mais votre application devra fournir ces informations pour pouvoir se connecter à la base de données. Par exemple, vous pouvez créer une boîte de dialogue qui invite l'utilisateur à fournir ces informations et génère dynamiquement la chaîne de connexion au moment de l'exécution. La sécurité peut encore être compromise si les informations sont interceptées sur le trajet vers la base de données.
Pour plus d’informations, consultez [Protection des informations de connexion](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Pour enregistrer une chaîne de connexion à partir de l’Assistant Configuration de Source de données
Dans le **Assistant de Configuration de Source de données**, sélectionnez l’option permettant d’enregistrer la connexion sur Enregistrer la chaîne de connexion à la page de fichier de Configuration d’Application.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Pour enregistrer une chaîne de connexion directement dans les paramètres de l'application
- Dans l’Explorateur de solutions, double-cliquez sur l’icône de mon projet (Visual Basic) ou l’icône de propriétés (c#) pour ouvrir le Concepteur de projet.
- Sélectionnez l’onglet Paramètres.
- Entrez un nom pour la chaîne de connexion. Faites référence à ce nom quand vous accédez à la chaîne de connexion dans le code.
- Définir le Type (chaîne de connexion).
- Laissez l’étendue définie sur l’Application.
- Tapez votre chaîne de connexion dans le champ de valeur, ou cliquez sur le bouton de sélection (...) dans le champ de valeur pour ouvrir la boîte de dialogue Propriétés de connexion pour générer votre chaîne de connexion.

## <a name="editing-connection-strings-stored-in-application-settings"></a>Modification des chaînes de connexion stockées dans les paramètres de l’application
Vous pouvez modifier les informations de connexion enregistrées dans les paramètres d’application à l’aide du Concepteur de projets.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Pour modifier une chaîne de connexion stockée dans les paramètres de l'application
- Dans l’Explorateur de solutions, double-cliquez sur l’icône de mon projet (Visual Basic) ou l’icône de propriétés (c#) pour ouvrir le Concepteur de projet.
- Sélectionnez l’onglet Paramètres.
- Localisez la connexion que vous souhaitez modifier, puis sélectionnez le texte dans le champ de valeur.
- Modifiez la chaîne de connexion dans le champ de valeur, ou cliquez sur le bouton de sélection (...) dans le champ de valeur pour modifier votre connexion à la boîte de dialogue Propriétés de connexion.

## <a name="editing-connection-strings-for-datasets"></a>Modification des chaînes de connexion pour les jeux de données
Vous pouvez modifier les informations de connexion pour chaque TableAdapter dans un dataset.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Pour modifier une chaîne de connexion pour un TableAdapter dans un dataset
- Dans l’Explorateur de solutions, double-cliquez sur le dataset (fichier .xsd) qui contient la connexion que vous souhaitez modifier.
- Sélectionnez le TableAdapter ou une requête qui contient la connexion que vous souhaitez modifier.
- Dans la fenêtre Propriétés, développez le nœud de connexion.
- Pour modifier rapidement la chaîne de connexion, modifiez la propriété ConnectionString, ou cliquez sur la flèche bas sur la propriété de connexion et cliquez sur Nouvelle connexion.

## <a name="security"></a>Sécurité
Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. Le recours à la sécurité intégrée de Windows est un moyen plus sûr de contrôler l'accès à une base de données.
Pour plus d’informations, consultez [Protection des informations de connexion](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Voir aussi

- [Ajout de connexions](../data-tools/add-new-connections.md)
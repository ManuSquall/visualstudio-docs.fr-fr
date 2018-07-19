---
title: 'Comment : enregistrer et modifier des chaînes de connexion'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 050d5f7bcda86890642a5bef10fa04d2c12b4203
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089229"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Comment : enregistrer et modifier des chaînes de connexion
Chaînes de connexion dans les applications Visual Studio sont enregistrées dans le fichier de configuration d’application (également appelé paramètres d’application) ou codées en dur directement dans votre application. L’enregistrement des chaînes de connexion dans le fichier de configuration de l’application simplifie la gestion de votre application. Si la chaîne de connexion doit être modifiée, vous pouvez le mettre à jour dans le fichier de paramètres d’application (par opposition à avoir à modifier dans le code source et recompiler l’application).

Le stockage d'informations sensibles (telles que le mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. Les chaînes de connexion enregistrées dans le fichier de configuration de l’application ne sont pas chiffrées ou obfusquées, il est donc possible pour quiconque d’accéder au fichier et d’afficher son contenu. Le recours à la sécurité intégrée de Windows est un moyen plus sûr de contrôler l'accès à une base de données.

Si vous choisissez de ne pas utiliser la sécurité intégrée de Windows et que votre base de données requiert un nom d'utilisateur et un mot de passe, vous pouvez l'omettre dans la chaîne de connexion, mais votre application devra fournir ces informations pour pouvoir se connecter à la base de données. Par exemple, vous pouvez créer une boîte de dialogue qui invite l'utilisateur à fournir ces informations et génère dynamiquement la chaîne de connexion au moment de l'exécution. La sécurité peut encore être compromise si les informations sont interceptées sur le trajet vers la base de données.
Pour plus d’informations, consultez [protégeant les informations de connexion](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Pour enregistrer une chaîne de connexion à partir de l’Assistant de Configuration de Source de données
Dans le **Assistant de Configuration de Source de données**, sélectionnez l’option pour enregistrer la connexion sur le **enregistrer la chaîne de connexion au fichier de Configuration de l’Application** page.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Pour enregistrer une chaîne de connexion directement dans les paramètres de l'application
1. Dans **l’Explorateur de solutions**, double-cliquez sur le **mon projet** icône (Visual Basic) ou **propriétés** icône (c#) pour ouvrir la **Concepteur de projet** .
1. Sélectionnez le **paramètres** onglet.
1. Entrez un **nom** pour la chaîne de connexion. Faites référence à ce nom quand vous accédez à la chaîne de connexion dans le code.
1. Définir le **Type** à (**chaîne de connexion**).
1. Laissez le **étendue** définie sur **Application**.
1. Tapez votre chaîne de connexion dans le **valeur** champ, ou cliquez sur le **points de suspension** bouton (...) dans le **valeur** champ pour ouvrir la **des propriétés de connexion** boîte de dialogue pour créer votre chaîne de connexion.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Modifier les chaînes de connexion stockées dans les paramètres d’application
Vous pouvez modifier les informations de connexion enregistrées dans les paramètres d’application à l’aide de la **Concepteur de projet**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Pour modifier une chaîne de connexion stockée dans les paramètres de l'application
1. Dans **l’Explorateur de solutions**, double-cliquez sur le **mon projet** icône (Visual Basic) ou **propriétés** icône (c#) pour ouvrir la **Concepteur de projet** .
1. Sélectionnez le **paramètres** onglet.
1. Localisez la connexion que vous souhaitez modifier, puis sélectionnez le texte dans le **valeur** champ.
1. Modifier la chaîne de connexion dans le **valeur** champ, ou cliquez sur le **points de suspension** bouton (...) dans le **valeur** champ pour modifier votre connexion avec le **connexion Propriétés** boîte de dialogue.

## <a name="edit-connection-strings-for-datasets"></a>Modifier les chaînes de connexion pour les jeux de données
Vous pouvez modifier les informations de connexion pour chaque TableAdapter dans un jeu de données.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Pour modifier une chaîne de connexion pour un TableAdapter dans un jeu de données
1. Dans **l’Explorateur de solutions**, double-cliquez sur le jeu de données (**.xsd** fichier) qui a la connexion que vous souhaitez modifier.
1. Sélectionnez le **TableAdapter** ou la requête qui a la connexion que vous souhaitez modifier.
1. Dans le **propriétés** fenêtre, développez le **nœud connexion**.
1. Pour modifier rapidement la chaîne de connexion, modifiez le **ConnectionString** propriété, ou cliquez sur la flèche vers le bas dans la **connexion** propriété et choisissez **nouvelle connexion**.

## <a name="security"></a>Sécurité
Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. Le recours à la sécurité intégrée de Windows est un moyen plus sûr de contrôler l'accès à une base de données.
Pour plus d’informations, consultez [protégeant les informations de connexion](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Voir aussi

- [Ajout de connexions](../data-tools/add-new-connections.md)
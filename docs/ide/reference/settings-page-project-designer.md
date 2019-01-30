---
title: Paramètres, page du Concepteur de projets
ms.date: 06/14/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fee0e6539901e5b95ca62f5e2beb1c3ea48692b0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958614"
---
# <a name="settings-page-project-designer"></a>Paramètres, page du Concepteur de projet

Utilisez la page **Paramètres** du Concepteur de projet pour spécifier les paramètres d’application d’un projet. Les paramètres d’application vous permettent de stocker et de récupérer des paramètres de propriétés et autres informations relatives à l’application de manière dynamique. Ils vous permettent également de tenir à jour des préférences utilisateur et d’application personnalisées sur un ordinateur client. Pour plus d’informations, consultez [Gérer les paramètres d’application](../managing-application-settings-dotnet.md).

Pour accéder à la page **Paramètres**, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis sélectionnez **Projet** > **Propriétés**. À l’affichage du Concepteur de projet, sélectionnez l’onglet **Paramètres**.

## <a name="header-bar"></a>Barre d’en-tête

La barre d’en-tête en haut de la page **Paramètres** contient plusieurs contrôles :

**Synchroniser**

**Synchroniser** restaure les paramètres de portée utilisateur utilisés par l’application au moment de l’exécution ou pendant le débogage à leurs valeurs par défaut telles que définies au moment du design. Pour restaurer les données, supprimez du disque (et non des données de projet) les fichiers propres à l’application générés au moment de l’exécution.

**Charger les paramètres web**

**Charger les paramètres web** affiche une boîte de dialogue **Connexion** qui vous permet de charger des paramètres pour un utilisateur authentifié ou pour des utilisateurs anonymes. Ce bouton est activé uniquement quand vous avez activé des services d’applications clientes dans la page **Services** et spécifié un **Emplacement des services de paramètres web**.

**Afficher le code**

Pour les projets C#, le bouton **Afficher le code** vous permet d’afficher le code dans le fichier *Settings.cs*. Ce fichier définit la classe `Settings`, qui vous permet de gérer des événements spécifiques sur l’objet `Settings`. Dans des langages autres que Visual Basic, vous devez appeler explicitement la méthode `Save` de cette classe wrapper pour conserver les paramètres utilisateur. Cela s’effectue habituellement dans le gestionnaire d’événements **Closing** du formulaire principal. Voici un exemple d’appel de la méthode `Save` :

```csharp
Properties.Settings.Default.Save();
```

Pour les projets Visual Basic, le bouton **Afficher le code** vous permet d’afficher le code dans le fichier *Settings.vb*. Ce fichier définit la classe `MySettings`, qui vous permet de gérer des événements spécifiques sur l’objet `My.Settings`. Pour plus d’informations sur l’accès aux paramètres d’application à l’aide de l’objet `My.Settings`, consultez [Accès aux paramètres d’application](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Pour plus d’informations sur l’accès aux paramètres d’application, consultez [Paramètres d’application pour les Windows Forms](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Modificateur d’accès** 

Le bouton **Modificateur d’accès** spécifie le niveau d’accès des classes d’assistance `Properties.Settings` (en C#) ou `My.Settings` (en Visual Basic) que Visual Studio génère dans *Settings.Designer.cs* ou *Settings.Designer.vb*.

Pour les projets Visual C#, le modificateur d’accès peut être **Internal** ou **Public**.

Pour les projets Visual Basic, le modificateur d’accès peut être **Friend** ou **Public**.

Par défaut, le paramètre est **Internal** en C# et **Friend** en Visual Basic. Quand Visual Studio génère des classes d’assistance **Internal** ou **Friend**, les applications exécutables (*.exe*) ne peuvent pas accéder aux ressources et aux paramètres que vous avez ajoutés aux bibliothèques de classes (fichiers *.dll*). Si vous devez partager des ressources et des paramètres à partir d’une bibliothèque de classes, affectez la valeur **Public** au modificateur d’accès.

Pour plus d’informations sur les classes d’assistance de paramètres, consultez [Gérer les paramètres d’application](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Grille de paramètres

La **grille de paramètres** sert à configurer les paramètres de l’application. Cette grille contient les colonnes suivantes :

**Name**

Entrez le nom du paramètre d’application dans ce champ.

**Type**

Utilisez la liste déroulante pour sélectionner un type pour le paramètre. Les types les plus fréquemment utilisés apparaissent dans la liste déroulante, par exemple **Chaîne**, **(Chaîne de connexion)** et **System.Drawing.Font**. Vous pouvez choisir un autre type en sélectionnant **Parcourir** à la fin de la liste, puis en sélectionnant dans la boîte de dialogue **Sélectionner un type**. Une fois que vous avez choisi un type, il est ajouté aux types communs dans la liste déroulante (pour la solution actuelle uniquement).

**Portée**

Sélectionnez **Application** ou **Utilisateur**.

Les paramètres de portée application, tels que les chaînes de connexion, sont associés à l’application. Les utilisateurs ne peuvent pas modifier les paramètres de portée application au moment de l’exécution.

Les paramètres de portée utilisateur, tels que les polices système, sont censés être utilisés pour les préférences utilisateur. Les utilisateurs peuvent les changer au moment de l’exécution.

**Valeur**

Données ou valeur associée(s) au paramètre d’application. Par exemple, si le paramètre est une police, sa valeur peut être **Verdana, 9.75pt, style=Bold**.

## <a name="see-also"></a>Voir aussi

- [Gérer les paramètres d’application](../managing-application-settings-dotnet.md)
- [Accéder aux paramètres d’application (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
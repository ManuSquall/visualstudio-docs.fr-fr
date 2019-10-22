---
title: Gestion des paramètres d’une application (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
ms.assetid: 35254321-ad14-47d9-b8c6-39ab3203c5d9
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b37ed78f9b67d10c0bf845a5bd7340f1f38557bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651422"
---
# <a name="managing-application-settings-net"></a>Gestion des paramètres d'une application (.NET)

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les paramètres d’application vous permettent de stocker des informations sur l’application de manière dynamique. Les paramètres vous permettent de stocker sur l’ordinateur client des informations qui ne doivent pas être incluses dans le code d’application (par exemple une chaîne de connexion), des préférences utilisateur et d’autres informations nécessaires au moment de l’exécution.

Les paramètres d’application remplacent les propriétés dynamiques utilisées dans les versions antérieures de Visual Studio.

Chaque paramètre d’application doit avoir un nom unique. Celui-ci peut être toute combinaison de lettres, de nombres ou de traits de soulignement, ne commençant pas par un nombre et ne contenant pas d’espaces. Le nom peut être modifié par le biais de la propriété `Name` .

Les paramètres d’application peuvent être stockés comme n’importe quel type de données sérialisable par XML ou ayant un `TypeConverter` qui implémente `ToString`/`FromString`. Les types les plus courants sont `String`, `Integer`et `Boolean`, mais vous pouvez également stocker des valeurs en tant que <xref:System.Drawing.Color>, <xref:System.Object>ou chaîne de connexion.

Les paramètres d’application contiennent également une valeur. La valeur est définie avec la propriété **Value** et doit correspondre au type de données du paramètre.

De plus, les paramètres d’application peuvent être liés à une propriété d’un formulaire ou d’un contrôle au moment du design.

Selon la portée, on distingue deux types de paramètres d’application :

- Les paramètres de portée application peuvent être utilisés pour des informations telles qu’une URL pour un service Web ou une chaîne de connexion à une base de données. Ces valeurs sont associées à l’application. Par conséquent, les utilisateurs ne peuvent pas les modifier au moment de l’exécution.

- Les paramètres de portée utilisateur peuvent être utilisés pour des informations telles que la persistance de la dernière position d’un formulaire ou d’une préférence de police. Les utilisateurs peuvent modifier ces valeurs au moment de l’exécution.

  Vous pouvez modifier le type d’un paramètre à l’aide de la propriété **Scope** .

  Le système de projet stocke les paramètres d’application dans deux fichiers XML : un fichier app.config, créé au moment du design lorsque vous créez le premier paramètre d’application ; et un fichier user.config, créé au moment de l’exécution lorsque l’utilisateur qui exécute l’application modifie la valeur d’un paramètre utilisateur. Notez que les modifications apportées aux paramètres utilisateur ne sont pas écrites sur le disque, sauf si l’application appelle spécifiquement une méthode pour le faire.

## <a name="creating-application-settings-at-design-time"></a>Créer les paramètres d’application au moment du design

Au moment du design, vous pouvez créer des paramètres d’application de deux manières : avec la page **Paramètres** du **Concepteur de projets**ou avec la fenêtre **Propriétés** pour un formulaire ou un contrôle, ce qui vous permet de lier un paramètre à une propriété.

Lorsque vous créez un paramètre de portée application (par exemple, une chaîne de connexion à une base de données ou une référence aux ressources du serveur), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] l’enregistre dans app.config avec la balise `<applicationSettings>` . (Les chaînes de connexion sont enregistrées sous la balise `<connectionStrings>` .)

Lorsque vous créez un paramètre de portée utilisateur (par exemple, une police par défaut, une page d’accueil ou une taille de fenêtre), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] l’enregistre dans app.config avec la balise `<userSettings>` .

> [!IMPORTANT]
> Lorsque vous stockez des chaînes de connexion dans app.config, vous devez prendre des précautions pour éviter de révéler des informations sensibles, telles que des mots de passe ou des chemins d’accès au serveur, dans la chaîne de connexion.
>
> Si vous obtenez une information de chaîne de connexion à partir d’une source externe, par exemple un utilisateur qui fournit un ID d’utilisateur et un mot de passe, vous devez veiller à ce que les valeurs utilisées pour construire votre chaîne de connexion ne contiennent pas de paramètres de chaîne de connexion supplémentaires qui modifient le comportement de votre connexion.
>
> Envisagez l’utilisation de la fonctionnalité de configuration protégée pour chiffrer les informations sensibles dans le fichier de configuration. Pour plus d’informations, consultez [Protection des informations de connexion](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).

> [!NOTE]
> Étant donné qu’il n’y a aucun modèle de fichier de configuration pour les bibliothèques de classes, les paramètres d’application ne s’appliquent pas aux projets Bibliothèque de classes. L’exception est un projet de DLL Visual Studio Tools pour Office, qui peut avoir un fichier de configuration.

## <a name="using-customized-settings-files"></a>Utilisation des fichiers de paramètres personnalisés

Vous pouvez ajouter des fichiers de paramètres personnalisés à votre projet pour une gestion pratique des groupes de paramètres. Comme les paramètres contenus dans un fichier unique sont chargés et enregistrés en tant qu’unité, la capacité à stocker les paramètres dans des fichiers séparés pour les groupes utilisés fréquemment et ceux utilisés rarement peut économiser du temps en termes de chargement et d’enregistrement des paramètres.

Par exemple, vous pouvez ajouter un fichier tel que SpecialSettings.settings à votre projet. Tandis que votre classe `SpecialSettings` n’est pas exposée dans l’espace de noms `My` , le mode **Afficher le code** peut lire le fichier des paramètres personnalisés qui contient `Partial Class SpecialSettings`.

Le Concepteur de paramètres recherche en premier le fichier Settings.settings que le système de projet crée ; il s’agit du fichier par défaut que le Concepteur de projets affiche dans l’onglet **Paramètres** . Settings.settings est localisé dans le dossier My Project pour les projets [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] et dans le dossier Propriétés pour les projets [!INCLUDE[csprcs](../includes/csprcs-md.md)] . Comme le Concepteur de projets recherche ensuite d’autres fichiers de paramètres dans le dossier racine du projet, vous devez mettre votre fichier de paramètres personnalisés à cet emplacement. Si vous ajoutez un fichier .settings ailleurs dans votre projet, le Concepteur de projets ne sera pas capable de le trouver.

## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Accéder ou modifier les paramètres d’application au moment de l’exécution en Visual Basic

Dans les projets [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , vous pouvez accéder aux paramètres d’application au moment de l’exécution à l’aide de l’objet `My.Settings` . Dans la page **Paramètres** , cliquez sur le bouton **Afficher le code** pour afficher le fichier Settings.vb. Settings.vb définit la classe `Settings` qui vous permet de gérer ces événements sur la classe de paramètres : <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>et <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Notez que la classe `Settings` dans Settings.vb est une classe partielle qui affiche uniquement le code appartenant à l’utilisateur, non pas l’intégralité de la classe générée. Pour plus d’informations sur l’accès aux paramètres d’application à l’aide de l’objet `My.Settings` , consultez [Accessing Application Settings](https://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e).

Les valeurs de tous les paramètres de portée utilisateur modifiés par l’utilisateur au moment de l’exécution (par exemple, la position d’un formulaire) sont stockées dans un fichier user.config. Notez que les valeurs par défaut restent enregistrées dans app.config.

Si vous avez modifié des paramètres de portée utilisateur au cours de l’exécution, en testant l’application par exemple, et souhaitez réinitialiser ces paramètres à leurs valeurs par défaut, cliquez sur le bouton **Synchroniser** .

Nous vous recommandons fortement d’utiliser l’objet `My.Settings` et le fichier .settings par défaut pour accéder aux paramètres. En effet, vous pouvez utiliser le Concepteur de paramètres pour assigner des propriétés aux paramètres ; en outre, les paramètres utilisateur sont enregistrés automatiquement avant l’arrêt de l’application. Toutefois, votre application [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] peut accéder directement aux paramètres. Dans ce cas, vous devez accéder à la classe `MySettings` et utiliser un fichier .settings personnalisé à la racine du projet. Vous devez également enregistrer les paramètres utilisateur avant de terminer l’application, comme vous le feriez pour une application C# (voir la section suivante).

<!-- markdownlint-disable MD003 MD020 -->
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>Accéder ou modifier les paramètres d’application au moment de l’exécution en Visual C#
<!-- markdownlint-enable MD003 MD020 -->

Dans les langages autres que [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], tels que [!INCLUDE[csprcs](../includes/csprcs-md.md)], vous devez accéder directement à la classe `Settings` , comme indiqué dans l’exemple [!INCLUDE[csprcs](../includes/csprcs-md.md)] suivant.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Vous devez également appeler explicitement la méthode `Save` de cette classe wrapper pour conserver les paramètres utilisateur. Cela s’effectue habituellement dans le gestionnaire d’événements `Closing` du formulaire principal. L’exemple [!INCLUDE[csprcs](../includes/csprcs-md.md)] suivant illustre un appel à la méthode `Save` .

```csharp
Properties.Settings.Default.Save();
```

Pour obtenir des informations générales sur l’accès aux paramètres d’application à l’aide de la classe `Settings`, consultez [Vue d’ensemble des paramètres d’application](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc). Pour plus d’informations sur l’itération au sein de paramètres, consultez ce [message de forum](http://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Voir aussi

- [Accès aux paramètres d’application](https://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)

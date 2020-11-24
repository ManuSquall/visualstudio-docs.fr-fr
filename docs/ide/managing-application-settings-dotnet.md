---
title: Gérer les paramètres d’application (.NET)
description: Apprenez à gérer les paramètres d’application (anciennement appelés propriétés dynamiques) qui ne sont pas inclus dans le code de l’application, mais qui sont nécessaires au moment de l’exécution.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62e03210e83f434bd32d08c3fe0f7b2b539155e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596896"
---
# <a name="manage-application-settings-net"></a>Gérer les paramètres d’application (.NET)

Les paramètres d’application vous permettent de stocker des informations sur l’application de manière dynamique. Les paramètres vous permettent de stocker des informations sur l’ordinateur client qui ne doivent pas être incluses dans le code de l’application (par exemple, une chaîne de connexion), des préférences utilisateur et d’autres informations dont vous avez besoin au moment de l’exécution.

Les paramètres d’application remplacent les propriétés dynamiques utilisées dans les versions antérieures de Visual Studio.

Chaque paramètre d’application doit avoir un nom unique. Celui-ci peut être toute combinaison de lettres, de nombres ou de traits de soulignement, ne commençant pas par un nombre et ne comportant pas d’espaces. Le nom est modifié par le biais de la propriété `Name`.

Les paramètres d’application peuvent être stockés comme n’importe quel type de données sérialisé par XML ou ayant un `TypeConverter` qui implémente `ToString`/`FromString`. Les types les plus courants sont `String`, `Integer`et `Boolean`, mais vous pouvez également stocker des valeurs en tant que <xref:System.Drawing.Color>, <xref:System.Object>ou chaîne de connexion.

Les paramètres d’application comportent également une valeur. La valeur est définie avec la propriété **Value** et doit correspondre au type de données du paramètre.

De plus, les paramètres d’application peuvent être liés à une propriété d’un formulaire ou d’un contrôle au moment du design.

Selon la portée, on distingue deux types de paramètres d’application :

- Les paramètres de portée application peuvent être utilisés pour des informations telles qu’une URL pour un service web ou une chaîne de connexion à une base de données. Ces valeurs sont associées à l’application. Par conséquent, les utilisateurs ne peuvent pas les modifier au moment de l’exécution.

- Les paramètres de portée utilisateur peuvent être utilisés pour des informations telles que la persistance de la dernière position d’un formulaire ou d’une préférence de police. Les utilisateurs peuvent modifier ces valeurs au moment de l’exécution.

Vous pouvez modifier le type d’un paramètre à l’aide de la propriété **Scope** .

Le système de projet stocke les paramètres d’application dans deux fichiers XML :

- Un fichier *app.config*, créé au moment du design quand vous créez le premier paramètre d’application

- Un fichier *user.config*, créé au moment de l’exécution quand l’utilisateur qui exécute l’application change la valeur d’un paramètre utilisateur

Notez que les modifications apportées aux paramètres utilisateur ne sont pas écrites sur le disque, sauf si l’application appelle spécifiquement une méthode pour le faire.

## <a name="create-application-settings-at-design-time"></a>Créer les paramètres d’application au moment du design

Au moment du design, vous pouvez créer des paramètres d’application de deux manières : avec la page **Paramètres** du **Concepteur de projets** ou avec la fenêtre **Propriétés** pour un formulaire ou un contrôle, ce qui vous permet de lier un paramètre à une propriété.

Lorsque vous créez un paramètre de portée application (par exemple, une chaîne de connexion à une base de données ou une référence aux ressources du serveur), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’enregistre dans *app.config* avec la `<applicationSettings>` balise. (Les chaînes de connexion sont enregistrées sous la balise `<connectionStrings>` .)

Lorsque vous créez un paramètre de portée utilisateur (par exemple, une police par défaut, une page d’hébergement ou une taille de fenêtre), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l’enregistre dans *app.config* avec la `<userSettings>` balise.

> [!IMPORTANT]
> Lorsque vous stockez des chaînes de connexion dans *app.config*, vous devez prendre des précautions pour éviter de révéler des informations sensibles, telles que les mots de passe ou les chemins d’accès au serveur, dans la chaîne de connexion.
>
> Si vous obtenez une information de chaîne de connexion à partir d’une source externe, par exemple un utilisateur qui fournit un ID d’utilisateur et un mot de passe, vous devez veiller à ce que les valeurs utilisées pour construire votre chaîne de connexion ne contiennent pas de paramètres de chaîne de connexion supplémentaires qui modifient le comportement de votre connexion.
>
> Envisagez l’utilisation de la fonctionnalité de configuration protégée pour chiffrer les informations sensibles dans le fichier de configuration. Pour plus d’informations, consultez [Protéger les informations de connexion](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Étant donné qu’il n’y a aucun modèle de fichier de configuration pour les bibliothèques de classes, les paramètres d’application ne s’appliquent pas aux projets Bibliothèque de classes. L’exception est un projet de DLL Visual Studio Tools pour Office, qui peut avoir un fichier de configuration.

## <a name="use-customized-settings-files"></a>Utiliser des fichiers de paramètres personnalisés

Vous pouvez ajouter des fichiers de paramètres personnalisés à votre projet pour une gestion pratique des groupes de paramètres. Comme les paramètres contenus dans un fichier unique sont chargés et enregistrés en tant qu’unité, Stocker les paramètres dans des fichiers séparés pour les groupes utilisés fréquemment et ceux utilisés rarement peut économiser du temps en termes de chargement et d’enregistrement des paramètres.

Par exemple, vous pouvez ajouter un fichier tel que *SpecialSettings. Settings* à votre projet. Tandis que votre classe `SpecialSettings` n’est pas exposée dans l’espace de noms `My` , le mode **Afficher le code** peut lire le fichier des paramètres personnalisés qui contient `Partial Class SpecialSettings`.

Le **Concepteur de paramètres** recherche en premier le fichier *Settings. Settings* que le système de projet crée ; ce fichier est le fichier par défaut que **le concepteur de projets** affiche dans l’onglet **paramètres** . Settings *. Settings* se trouve dans le dossier *My Project* pour les [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projets et dans le dossier *Propriétés* pour les [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projets. Le **Concepteur de projets** recherche ensuite d’autres fichiers de paramètres dans le dossier racine du projet. vous devez mettre votre fichier de paramètres personnalisés à cet emplacement. Si vous ajoutez un fichier *. Settings* ailleurs dans votre projet, le **Concepteur de projets** ne sera pas en mesure de le localiser.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Accéder aux paramètres d’application, ou les changer, au moment de l’exécution en Visual Basic

Dans les projets Visual Basic, vous pouvez accéder aux paramètres d’application au moment de l’exécution à l’aide de l’objet `My.Settings`. Sur la page **paramètres** , cliquez sur le bouton **afficher le code** pour afficher le fichier *Settings. vb* . *Settings. vb* définit la `Settings` classe, qui vous permet de gérer ces événements sur la classe de paramètres : <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> , <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged> , <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded> et <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> . Notez que la `Settings` classe dans *Settings. vb* est une classe partielle qui affiche uniquement le code appartenant à l’utilisateur, et non l’intégralité de la classe générée. Pour plus d’informations sur l’accès aux paramètres d’application à l’aide de l’objet `My.Settings`, consultez [Accéder aux paramètres d’application (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Les valeurs de tous les paramètres de portée utilisateur modifiés par l’utilisateur au moment de l’exécution (par exemple, la position d’un formulaire) sont stockées dans un fichier de *user.config* . Notez que les valeurs par défaut sont toujours enregistrées dans *app.config*.

Si des paramètres de portée utilisateur sont changés au cours de l’exécution, à l’occasion d’un test de l’application par exemple, et que vous souhaitez réinitialiser ces paramètres à leurs valeurs par défaut, cliquez sur le bouton **Synchroniser**.

Nous vous recommandons vivement d’utiliser l' `My.Settings` objet et le fichier *. Settings* par défaut pour accéder aux paramètres. Cela est dû au fait que vous pouvez utiliser le **Concepteur de paramètres** pour assigner des propriétés aux paramètres et, en outre, les paramètres utilisateur sont enregistrés automatiquement avant l’arrêt de l’application. Toutefois, votre application Visual Basic peut accéder directement aux paramètres. Dans ce cas, vous devez accéder à la `MySettings` classe et utiliser un fichier *. Settings* personnalisé à la racine du projet. Vous devez enregistrer les paramètres utilisateur avant de terminer l’application, comme vous le feriez pour une application C# (voir la section suivante).

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Accéder aux paramètres d’application, ou les changer, au moment de l’exécution en C#
<!-- markdownlint-enable MD003 MD020 -->

Dans les langages autres que Visual Basic, tels que C#, vous devez accéder directement à la classe `Settings`, comme indiqué dans l’exemple [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] suivant.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Vous devez appeler explicitement la méthode `Save` de cette classe wrapper pour conserver les paramètres utilisateur. Cela s’effectue habituellement dans le gestionnaire d’événements `Closing` du formulaire principal. L’exemple C#, suivant illustre un appel à la méthode `Save`.

```csharp
Properties.Settings.Default.Save();
```

Pour obtenir des informations générales sur l’accès aux paramètres d’application à l’aide de la classe `Settings`, consultez [Présentation des paramètres d’application (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Pour plus d’informations sur l’itération au sein de paramètres, consultez ce [message de forum](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Voir aussi

- [Accéder aux paramètres d’application (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)

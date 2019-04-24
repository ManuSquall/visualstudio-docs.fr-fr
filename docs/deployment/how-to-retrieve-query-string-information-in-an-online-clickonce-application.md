---
title: 'Procédure : Récupérer les informations de chaîne de requête dans une Application ClickOnce en ligne | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e218cfb3514333e48f2c5d59d55664de1bbd906a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095854"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Procédure : Récupérer les informations de chaîne de requête dans une application ClickOnce en ligne
La *chaîne de requête* est la partie d’une URL commençant par un point d’interrogation ( ?) qui contient des informations arbitraires sous la forme *nom=valeur*. Supposez que vous avez une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nommée `WindowsApp1` que vous hébergez sur `servername`, et que vous souhaitez passer une valeur pour la variable `username` quand l’application démarre. Votre code peut ressembler à ce qui suit :

 `http://servername/WindowsApp1.application?username=joeuser`

 Les deux procédures suivantes montrent comment utiliser une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pour obtenir les informations de chaîne de requête.

> [!NOTE]
>  Vous pouvez passer des informations dans une chaîne de requête quand votre application est lancée uniquement à l’aide du protocole HTTP, au lieu d’utiliser un partage de fichiers ou le système de fichiers local.

 La première procédure montre comment votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peut utiliser un petit bloc de code pour lire ces valeurs au démarrage de l’application.

 La procédure suivante montre comment configurer votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l’aide de MageUI.exe pour qu’elle accepte des paramètres de chaîne de requête. Vous devez effectuer ces opérations chaque fois que vous publiez votre application.

> [!NOTE]
>  Avant de décider d’activer cette fonctionnalité, consultez la section « Sécurité » plus loin dans cette rubrique.

 Pour plus d’informations sur la création d’un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l’aide du déploiement *Mage.exe* ou *MageUI.exe*, consultez [procédure pas à pas : Déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

> [!NOTE]
>  À compter du .NET Framework 3.5 SP1, vous pouvez passer des arguments de ligne de commande à une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] hors connexion. Si vous souhaitez fournir des arguments à l’application, vous pouvez passer des paramètres au fichier de raccourci avec l’extension .APPREF-MS.

### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Pour obtenir des informations de chaîne de requête à partir d’une application ClickOnce

1. Placez le code suivant dans votre projet. Pour que ce code fonctionne, vous devez avoir une référence à System.Web et ajouter des instructions `using` ou `Imports` pour System.Web, System.Collections.Specialized et System.Deployment.Application.

     [!code-csharp[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]

2. Appelez la fonction précédemment définie pour récupérer un <xref:System.Collections.DictionaryBase.Dictionary%2A> des paramètres de chaîne de requête, indexés par nom.

### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Pour activer le transfert de chaînes de requête dans une application ClickOnce avec MageUI.exe

1. Ouvrez l’invite de commandes .NET et tapez :

   ```cmd
   MageUI
   ```

2. Dans le menu **Fichier** , sélectionnez **Ouvrir**et ouvrez le manifeste de déploiement pour votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , c’est-à-dire le fichier se terminant par l’extension `.application` .

3. Sélectionnez le panneau **Options de déploiement** dans la fenêtre de navigation de gauche, puis cochez la case **Autoriser le transfert des paramètres d’URL vers l’application** .

4. Dans le menu **Fichier** , sélectionnez **Enregistrer**.

> [!NOTE]
>  Vous pouvez également activer le transfert des chaînes de requête dans [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Cochez la case **Autoriser le transfert des paramètres d’URL vers l’application** , accessible en ouvrant les **Propriétés du projet**, en sélectionnant l’onglet **Publier** , en cliquant sur le bouton **Options** , puis en sélectionnant **Manifestes**.

## <a name="robust-programming"></a>Programmation fiable
 Quand vous utilisez des paramètres de chaîne de requête, vous devez faire attention à la façon dont votre application est installée et activée. Si votre application est configurée pour s’installer sur l’ordinateur de l’utilisateur à partir du web ou d’un partage réseau, il est probable que l’utilisateur activera l’application une seule fois par le biais de l’URL. Après cela, il l’activera généralement à l’aide du raccourci dans le menu **Démarrer** . Ainsi, votre application est assurée de recevoir des arguments de chaîne de requête une seule fois pendant sa durée de vie. Si vous choisissez de stocker ces arguments sur l’ordinateur de l’utilisateur pour une utilisation ultérieure, vous devez les stocker de manière sûre et sécurisée.

 Si votre application est uniquement en ligne, elle sera toujours activée par le biais d’une URL. Même dans ce cas, toutefois, votre application doit être écrite pour fonctionner correctement si les paramètres de chaîne de requête sont manquants ou endommagés.

## <a name="net-framework-security"></a>sécurité du .NET Framework
 Autorisez le transfert des paramètres d’URL à votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uniquement si vous envisagez de nettoyer l’entrée de caractères malveillants avant de l’utiliser. Une chaîne incorporée avec des guillemets, des barres obliques ou des points-virgules, par exemple, peut effectuer des opérations de données arbitraires si elle est utilisée sans filtre dans une requête SQL sur une base de données. Pour plus d’informations sur la sécurité des chaînes de requête, consultez [Script Exploits Overview](https://msdn.microsoft.com/Library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).

## <a name="see-also"></a>Voir aussi
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
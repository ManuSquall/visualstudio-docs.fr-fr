---
title: Codes d’erreur pour les applications Windows Runtime utilisant JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 05/10/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- JavaScript, Windows Runtime error codes
- VS.WebClient.Help.APPHOST9601
- VS.WebClient.Help.APPHOST9602
- VS.WebClient.Help.APPHOST9603
- VS.WebClient.Help.APPHOST9604
- VS.WebClient.Help.APPHOST9605
- VS.WebClient.Help.APPHOST9606
- VS.WebClient.Help.APPHOST9607
- VS.WebClient.Help.APPHOST9608
- VS.WebClient.Help.APPHOST9610
- VS.WebClient.Help.APPHOST9611
- VS.WebClient.Help.APPHOST9613
- VS.WebClient.Help.APPHOST9614
- VS.WebClient.Help.APPHOST9615
- VS.WebClient.Help.APPHOST9616
- VS.WebClient.Help.APPHOST9617
- VS.WebClient.Help.APPHOST9618
- VS.WebClient.Help.APPHOST9619
- VS.WebClient.Help.APPHOST9620
- VS.WebClient.Help.APPHOST9623
- VS.WebClient.Help.APPHOST9624
- VS.WebClient.Help.APPHOST9626
ms.assetid: 4c6d4e90-602a-4b56-ae74-3458929da442
caps.latest.revision: 1
author: erikadoyle
ms.author: edoyle
manager: jken
ms.openlocfilehash: 89b91a3246d0a6e2980459c2c35c7361168bccd4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571509"
---
# <a name="error-codes-for-windows-runtime-apps-using-javascript"></a>Codes d’erreur pour les applications Windows Runtime utilisant JavaScript
Voici les codes d’erreur affichés par la console Microsoft Visual Studio durant le développement d’applications Windows Runtime en JavaScript.
  
Erreur | Remarques
----- | -------
APPHOST9601 : « Impossible de charger *remoteURI*. Une application ne peut pas charger du contenu Web distant dans le contexte local. » | Pour plus d’informations sur ce qui est autorisé dans le contexte web, consultez [Fonctionnalités et restrictions par contexte](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9602 : « 'javascript:' est une valeur d’attribut non valide. Elle sera ignorée. N’utilisez pas d’URI 'javascript:' dans le contexte local. » | Pour des raisons de sécurité, vous ne pouvez pas utiliser les URI 'javascript:' dans le contexte local. Pour plus d’informations sur ce qui est autorisé dans le contexte local, consultez [Fonctionnalités et restrictions par contexte](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9603 : « Impossible de charger le plug-in ActiveX ayant l’ID de classe *classID*.  Les applications ne peuvent pas charger des contrôles ActiveX. » | Les applications Windows Runtime en JavaScript ne prennent pas en charge les contrôles Microsoft ActiveX personnalisés. Si vous avez besoin d’un contrôle d’interface utilisateur, utilisez un contrôle web standard ou une bibliothèque de contrôles, ou créez un contrôle personnalisé. Si vous devez exécuter une logique personnalisée, créez un objet Windows Runtime personnalisé à la place. Pour plus d’informations sur les autres différences avec HTML, CSS et JavaScript, consultez [Fonctionnalités et différences HTML, CSS et JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9604 : « Impossible de naviguer vers *uri*, car il contient un encodage de caractères non valide.  Une application peut uniquement naviguer vers des fichiers UTF-8. » | Si Windows Runtime accède à du code HTML, JavaScript et CSS, celui-ci doit être encodé au format UTF-8 (Unicode Transformation Format) 8 bits. Pour plus d’informations sur les autres différences avec HTML, CSS et JavaScript, consultez [Fonctionnalités et différences HTML, CSS et JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9605 : « Impossible de naviguer vers *targetURI* depuis *sourceURI*, car l’URI de destination est dans une zone de sécurité plus élevée. Vous ne pouvez pas naviguer vers une zone de sécurité plus élevée depuis une zone de sécurité plus faible, sauf si vous naviguez vers un URI de contexte local depuis un URI de contexte Web et que vous avez inscrit l’URI de contexte local avec la méthode MSApp.addPublicLocalApplicationUri. » | Pour plus d’informations, consultez [MSApp.addPublicLocalApplicationUri](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465759.aspx).
APPHOST9606 : « Impossible de charger *uri* en raison de l’utilisation d’une connexion HTTP et de la présence de l’élément META ms-https-connections-only. Seules les connexions HTTPS sont autorisées lorsque vous utilisez l’élément META ms-https-connections-only. Utilisez une connexion HTTPS ou, si vous n’avez pas besoin d’une connexion sécurisée, supprimez l’élément META. » | Pour plus d’informations, consultez [Guide pratique pour exiger une connexion HTTPS](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9607 : « L’application ne peut pas lancer l’URI à l’emplacement *uri* en raison de l’erreur suivante : *failureCode*. » | Des ressources manquantes ou des fichiers non valides sont des causes courantes de cette erreur.
APPHOST9608 : « L’application n’a pas pu naviguer vers la page about:blank en raison de l’erreur suivante : *errorCode*. » | 
APPHOST9610 : « L’application a rencontré une erreur lors de la préparation de la navigation vers une page d’erreur personnalisée : *errorCode*. » |
APPHOST9611 : « L’application n’a pas pu naviguer vers une page d’erreur personnalisée en raison de l’erreur suivante : *errorCode*. » |
APPHOST9613 : « L’application n’a pas pu naviguer vers * uri* en raison de l’erreur suivante : *errorCode*. » | 
APPHOST9614 : « Un document dans un iframe a demandé le mode de document *requestedDocMode* alors que le système applique le mode de document *currentDocMode*. L’iframe utilisera le mode de document *currentDocMode*. » | Pour plus d’informations sur l’affichage du contenu web à distance, consultez [Guide pratique pour créer des liens vers des pages web externes](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9615 : « L’application ne peut pas télécharger le fichier à l’emplacement *uri*, car il a été appelé par programmation en dehors du contexte local. » | Se produit quand du contenu dans le contexte web tente de télécharger un fichier par programmation.
APPHOST9616 : « Cet URI ne peut pas utiliser les API de géolocalisation.  Les API de géolocalisation peuvent uniquement être appelées à partir d’un URI qui fait partie du package ou qui est inclus dans l’élément ApplicationContentUris du manifeste. » | Pour plus d’informations sur ce qui est autorisé dans le contexte web, consultez [Fonctionnalités et restrictions par contexte](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9617 : « Cet URI ne peut pas utiliser les API de Presse-papiers.  Les API de Presse-papiers peuvent uniquement être appelées à partir d’un URI qui fait partie du package ou qui est inclus dans l’élément ApplicationContentUris du manifeste. » | Pour plus d’informations sur ce qui est autorisé dans le contexte web, consultez [Fonctionnalités et restrictions par contexte](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9618 : « Cet URI ne peut pas utiliser window.close.  La méthode window.close peut uniquement être appelée à partir d’un contenu packagé qui a été chargé avec un schéma d’URI ms-appx. » | Pour plus d’informations sur ce qui est autorisé dans le contexte web, consultez [Fonctionnalités et restrictions par contexte](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9619 : « L’application ne peut pas naviguer vers *uri*, car une page du contexte web ne peut pas être le document de niveau supérieur de l’application. Chargez la page dans un iframe à la place. » | Vous ne pouvez pas naviguer vers une page web à distance à partir de votre page de niveau supérieur, mais votre application peut afficher une page web dans un [iframe](https://msdn.microsoft.com/en-us/library/ms535258(v=vs.85).aspx). Pour plus d’informations sur l’affichage du contenu web à distance, consultez [Guide pratique pour créer des liens vers des pages web externes](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9620 : « Cette application a été fermée, car elle utilisait une connexion HTTP alors que l’élément META ms-https-connections-only est présent. Seules les connexions HTTPS sont autorisées lorsque vous utilisez l’élément META ms-https-connections-only. Utilisez une connexion HTTPS ou, si vous n’avez pas besoin d’une connexion sécurisée, supprimez l’élément META. » | Pour plus d’informations, consultez [Guide pratique pour exiger une connexion HTTPS](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9623 : « L’application n’a pas pu résoudre *url* en raison de l’erreur suivante : *errorCode*. » | Un fichier manquant est une cause courante de cette erreur.  
APPHOST9624 : « L’application ne peut pas utiliser de script pour charger l’URL *url*, car cette dernière lance une autre application. Seule une interaction directe avec l’utilisateur peut lancer une autre application. » | Les applications ne peuvent pas lancer d’autres applications directement. L’utilisateur peut lancer d’autres applications quand l’application implémente certains contrats. Pour plus d’informations, consultez [Contrats et extensions des applications](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh464906.aspx).
APPHOST9626 : « Une référence directe au fichier de ressources `ms-appx://1d33240b-0b00-40e4-a416-a4750c48787f/ja-jp\images\logo.scale-140.png` a été détectée. Cette référence pose des problèmes lorsqu’elle est utilisée en dehors de l’environnement de débogage. » | En raison du chemin de `logo.scale-140.png`, ce fichier PNG est traité comme une ressource localisée. Il en résulte une erreur car les ressources localisées ne peuvent pas être référencées directement. Si vous envisagez d’utiliser ce fichier comme ressource de langue, consultez [Globalisation de votre application (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465006.aspx). Sinon, essayez de renommer le répertoire qui pose problème.
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de Windows Runtime dans JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
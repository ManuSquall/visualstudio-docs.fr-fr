---
ms.openlocfilehash: 3ffab1767817189c8bf27c699713354979425d21
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101750755"
---
## <a name="prerequisites"></a>Prérequis

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) installé avec les charges de travail appropriées pour le langage de votre choix :
  * ASP.NET : **Développement web et ASP.NET**
  * Node.js : **Développement Node.js**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) installé avec les charges de travail appropriées pour le langage de votre choix :
  * ASP.NET : **Développement web et ASP.NET**
  * Node.js : **Développement Node.js**
::: moniker-end

* Un abonnement Azure. Si vous n’avez pas encore d’abonnement, [inscrivez-vous gratuitement](https://azure.microsoft.com/free/dotnet/) et bénéficiez de 200 $ de crédit pendant 30 jours et de 12 mois de services gratuits.

* Un projet ASP.NET, ASP.NET Core, .NET Core ou Node.js. Si vous n’avez pas encore de projet, sélectionnez une option ci-dessous :
  * ASP.NET Core : suivre [le Guide de démarrage rapide : utilisez Visual Studio pour créer votre première application web ASP.net Core](../../ide/quickstart-aspnet-core.md)ou procédez comme suit :
    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, choisissez **créer un nouveau projet** dans la fenêtre démarrer. Si la fenêtre de démarrage n’est pas ouverte , choisissez  >  **fenêtre démarrage** de fichier. Tapez **application Web** dans la zone de recherche, choisissez **C#** comme langue, puis **ASP.net Core application Web (Model-View-Controller)**, puis choisissez **suivant**. Dans l’écran suivant, nommez le projet **MyASPApp**, puis choisissez **suivant**.

    Choisissez le Framework cible recommandé (.NET Core 3,1) ou .NET 5, puis choisissez **créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans Visual Studio 2017, choisissez **fichier**  >  **nouveau projet**, sélectionnez **Visual C#**  >  **.net Core**, puis sélectionnez **ASP.net Core application Web**. À l’invite, sélectionnez le modèle **Application web (Model-View-Controller)**, vérifiez que l’option **Aucune authentification** est activée, puis sélectionnez **OK**.
    ::: moniker-end
  * Node.js : suivez [Démarrage rapide : utiliser Visual Studio pour créer votre première application Node.js](../../ide/quickstart-nodejs.md), ou utilisez **Fichier** > **Nouveau projet**, sélectionnez **JavaScript**, puis **Application web Node.js vide**.

* N’oubliez pas de générer le projet à l’aide de la commande de menu **Générer > Générer la solution** avant de suivre les étapes de déploiement.
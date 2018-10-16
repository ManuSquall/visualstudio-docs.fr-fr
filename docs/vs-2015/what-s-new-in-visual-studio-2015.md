---
title: Ce que&#39;s dans Visual Studio 2015 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
caps.latest.revision: 364
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f97369709390d6a3e98ff8d995000d6edc574b13
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226165"
---
# <a name="what39s-new-in-visual-studio-2015"></a>Ce que&#39;s dans Visual Studio 2015
[!INCLUDE[vs2017banner](./includes/vs2017banner.md)]

Bienvenue dans Visual Studio 2015, une suite intégrée d'outils de productivité pour les développeurs, de services cloud et d'extensions qui vous permettent, à vous et votre équipe, de créer de superbes applications et de magnifiques jeux pour le web, le Windows Store, le Bureau, Android et iOS.  
  
 Cette page présente certaines des fonctionnalités les plus importantes apparues depuis Visual Studio 2013 RTM, y compris les fonctionnalités introduites dans les mises à jour de Visual Studio 2013. Pour obtenir la liste complète des nouveautés de Visual Studio 2015, consultez [Notes de publication](https://www.visualstudio.com/news/vs2015-vs).  
  
 Pour en savoir plus sur les nombreuses améliorations et nouvelles fonctionnalités de Visual Studio ALM, consultez [Nouveautés d'Application Lifecycle Management dans Visual Studio 2015](http://msdn.microsoft.com/en-us/54b98a53-6083-4303-869a-8063d8fae938).  
  
## <a name="a-new-setup-experience"></a>Une nouvelle expérience d'installation  
 [!INCLUDE[downloadvs](./includes/downloadvs-md.md)]  
  
 L'expérience d'installation de Visual Studio 2015 a été organisée en composants pour que vous n'ayez à installer que les composants dont vous avez besoin. Cela accélère l'installation pour de nombreux scénarios courants impliquant le développement web ou .NET. Si vous effectuez d'autres types de développement, tels que le développement multiplateforme pour appareils mobiles, ou que vous travaillez en C++ ou F#, choisissez l'installation **Personnalisée** , puis les composants et les Kits SDK facultatifs tiers dont vous avez besoin. Vous pouvez également installer les composants personnalisés ultérieurement. Par exemple, si vous choisissez l'installation de base et que vous tentez ensuite de créer un projet C++, vous serez invité à télécharger les outils de développement C++.  
  
 ![Boîte de dialogue d’installation Visual Studio 2015](./ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")  
  
## <a name="sign-in-across-multiple-accounts"></a>Se connecter sur plusieurs comptes  
 Avec Visual Studio 2015, la nouvelle expérience de connexion simplifiée est conçue pour simplifier considérablement l'accès aux ressources en ligne, même si vous possédez plusieurs comptes Visual Studio. Une fois connecté à Visual Studio, vous êtes automatiquement connecté à toutes les instances de Visual Studio 2015 et de Blend sur votre ordinateur. La connexion démarre automatiquement l'itinérance de vos paramètres. Dans Visual Studio 2015, votre compte est partagé entre les différentes fonctionnalités. Ainsi, tant que vous disposez d’un jeton approprié, vous pouvez accéder à vos comptes Visual Studio Team Services à partir de **Team Explorer**, ainsi qu’aux ressources et sites web de votre abonnement Microsoft Azure dans l’Explorateur de serveurs. Vos ressources Azure sont aussi visibles dans la boîte de dialogue Nouveau projet pour les projets Application Insights. Quant à vos comptes Azure Mobile, Azure Storage, [Microsoft Office 365](http://msdn.microsoft.com/office/aa905340.aspx) et [développeur Saleforce.com](https://developer.salesforce.com/) , ils sont répertoriés dans la nouvelle boîte de dialogue **Ajouter un service connecté** .  
  
 Vous pouvez utiliser plusieurs comptes d'utilisateur dans Visual Studio en les ajoutant au fur et à mesure ou en recourant au nouveau gestionnaire de comptes. Vous pouvez ensuite passer d'un compte à un autre, à la volée, quand vous vous connectez aux services ou quand vous accédez aux ressources en ligne. Visual Studio mémorise les comptes que vous ajoutez pour que vous puissiez les utiliser à partir de n'importe quelle instance de Visual Studio ou Blend. Visual Studio saura également rendre itinérante la liste des comptes (toutefois, nous n'allons pas rendre itinérantes vos informations d'identification importantes) avec votre compte de personnalisation pour que vous puissiez rapidement commencer à utiliser l'un de ces comptes sur un autre appareil. Bien sûr, vous pouvez supprimer des comptes à partir de la boîte de dialogue Paramètres de compte, à tout moment. Pour commencer, consultez [Work with multiple user accounts](./ide/work-with-multiple-user-accounts.md).  
  
 ![Gestionnaire de comptes](./ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")  
  
## <a name="choose-your-target-platforms"></a>Choisir vos plateformes cibles  
 Visual Studio 2015 prend en charge le développement multiplateforme pour appareils mobiles. Vous pouvez écrire des applications et des jeux qui ciblent iOS, Android et Windows, et qui partagent une base de code commune, le tout à partir de l'IDE de Visual Studio. Vous verrez tous ces nouveaux types de projet dans la boîte de dialogue Fichier, Nouveau projet.  
  
 Naturellement, la prise en charge des applications de bureau classiques est optimale, grâce aux nombreuses améliorations apportées aux langages, bibliothèques et outils.  
  
### <a name="cross-platform-mobile-apps-in-c-with-xamarin-for-visual-studio"></a>Applications mobiles multiplateformes en C# avec Xamarin pour Visual Studio  
 Xamarin est une infrastructure mobile. Elle vous permet d'écrire du code en C# qui se lie de façon native aux API iOS et Android. Microsoft a conclu un partenariat en étroite collaboration avec Xamarin concernant leur version de Xamarin pour Visual Studio, une extension qui vous permet de développer pour Android, iOS et Windows Phone dans une seule solution avec du code partagé. Avec Xamarin, vous utiliserez un langage et une base de code avec des deltas minimaux entre les plateformes.  Xamarin pour Visual Studio est pris en charge par Visual Studio 2010 et versions ultérieures. L’édition starter de Xamarin est incluse dans Visual Studio 2015. Pour commencer, consultez [créer des applications avec une interface utilisateur native à l’aide de Xamarin dans Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md).  
  
### <a name="cross-platform-mobile-apps-in-htmljavascript-with-apache-cordova"></a>Applications mobiles multiplateformes en HTML/JavaScript avec Apache Cordova  
 Visual Studio Tools pour Apache Cordova est le fruit d'une étroite collaboration entre Microsoft et la communauté Open Source d'Apache Cordova. Ces outils permettent le développement multiplateforme pour appareils mobiles en HTML, CSS et JavaScript (ou TypeScript). Vous pouvez cibler des plateformes Android, iOS et Windows avec une base de code unique, et tirer parti de la richesse de l'IDE de Visual Studio, notamment avec JavaScript IntelliSense, l'explorateur DOM, la console JavaScript, les points d'arrêt, les espions, les variables locales, Uniquement mon code, etc.  Avec Visual Studio Tools pour Apache Cordova, vos applications ont accès aux fonctionnalités natives des appareils sur toutes les plateformes grâce à des plug-ins qui fournissent une API JavaScript commune. Pour commencer, consultez [bien démarrer avec Visual Studio Tools pour Apache Cordova](http://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42).  
  
### <a name="cross-platform-mobile-games-in-c-with-unity"></a>Jeux mobiles multiplateformes en C# avec Unity  
 Unity est une plateforme largement utilisée pour le développement de jeux 2D et 3D multiplateforme. Vous pouvez écrire votre jeu en C# et l'exécuter de façon native sur Android, iOS, Windows Phone et de nombreuses autres plateformes. Visual Studio Tools for Unity est une extension qui intègre Unity à l'IDE de Visual Studio. Avec cette extension, vous obtenez toutes les fonctionnalités de l'IDE de Visual Studio et de son débogueur, en plus des fonctionnalités de productivité conçues pour les développeurs Unity. Visual Studio Tools for Unity 2.0 Preview 2 ajoute la prise en charge de Visual Studio 2015 et d'un certain nombre de nouvelles fonctionnalités, notamment une meilleure visualisation des objets dans les fenêtres Variables locales et Espion. Microsoft a récemment acquis SyntaxTree, la société des créateurs de Visual Studio Tools for Unity. Pour télécharger Visual Studio Tools for Unity 2.0 Preview 2 et pour plus d’informations sur Visual Studio Tools for Unity, consultez [Visual Studio Tools for Unity 2.0](http://Aka.ms/vstu).  
  
### <a name="cross-platform-apps-and-libraries-for-native-c"></a>Applications et bibliothèques multiplateformes pour du code C++ natif  
 C++ est un langage disponible en mode natif sur la plupart des appareils mobiles. Vous pouvez l'utiliser pour écrire des bibliothèques de code partagé multiplateformes qui peuvent être générées pour plusieurs plateformes mobiles cibles. Vous pouvez même créer des applications mobiles tout en C++. Visual C++ offre les outils nécessaires pour modifier, générer, déployer et déboguer votre code multiplateforme. Outre les modèles pour les applications Windows, vous pouvez créer des projets à partir de modèles pour des applications Android Native Activity, des applications iOS ou des projets de bibliothèque de code partagé pour plusieurs plateformes qui incluent des applications hybrides Xamarin. La technologie IntelliSense spécifique à la plateforme vous permet d'explorer les API et de générer le code approprié pour des cibles Android, iOS ou Windows. Vous pouvez configurer votre build pour les plateformes natives x86 ou ARM et déployer votre code dans un simulateur iOS ou sur des appareils iOS sur un Mac connecté au réseau, sur des appareils Android directement connectés, ou exploiter les performances de l'émulateur Microsoft Visual Studio pour Android à des fins de test. Vous pouvez définir des points d'arrêt, espionner des variables, consulter la pile et exécuter le code C++ pas à pas dans le débogueur Visual Studio. Vous pouvez partager tout le code (hormis le plus spécifique à une plateforme) entre plusieurs plateformes d'applications, puis générer l'ensemble avec une seule solution dans Visual Studio.  
  
 Pour commencer sur inter-plateformes C++, consultez [générer des applications mobiles multiplateformes avec Visual C++](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)  
  
### <a name="universal-windows-apps-for-any-windows-10-device"></a>Applications Windows universelles pour tout appareil Windows 10  
 Avec la plateforme Windows universelle et notre noyau Windows, vous pouvez exécuter la même application sur n'importe quel appareil Windows 10, des téléphones jusqu'aux ordinateurs de bureau. Créez ces applications Windows universelles avec Visual Studio 2015 et les outils de développement d’applications Windows universelles.  
  
 ![Plateforme Windows universelle](./cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")  
  
 Exécutez votre application sur un téléphone Windows 10, un poste de travail Windows 10 ou une console Xbox. C’est le même package d’application ! Avec l’introduction d’un noyau unifié unique dans Windows 10, le même package d’application peut s’exécuter sur toutes les plateformes. Plusieurs plateformes ont des kits de développement logiciel (SDK) Extension que vous pouvez ajouter à votre application pour tirer parti des comportements spécifiques à une plateforme. Par exemple, un SDK d’extension pour mobile gère le comportement du bouton Précédent sur un Windows Phone. Si vous référencez un SDK d’extension dans votre projet, il vous suffit ensuite d’ajouter des vérifications à l’exécution pour vérifier si ce SDK est disponible sur cette plateforme. C’est comme cela que vous pouvez utiliser le même package d’application pour toutes les plateformes !  
  
 Utilisez le langage C#, Visual Basic, C++ ou JavaScript pour créer des [applications Windows universelles](http://msdn.microsoft.com/library/dn975273.aspx).  
  
### <a name="web"></a>Web  
 ASP.NET 5 est une mise à jour majeure de MVC, WebAPI et SignalR, et s'exécute sur Windows, Mac et Linux.  ASP.NET 5 a été conçu de toutes pièces pour vous fournir une pile .NET adaptée et composable pour la génération d'applications cloud modernes. Les outils de Visual Studio 2015 sont intégrés plus étroitement aux outils de développement web populaires tels que Bower et Grunt. Pour commencer, consultez les nombreuses publications de blog sur le  [blog relatif aux outils et au développement web .NET](http://blogs.msdn.com/b/webdev/).  
  
### <a name="classic-desktop-and-windows-store"></a>Bureau classique et Windows Store  
 Visual Studio 2015 continue à prendre en charge le développement d'applications de bureau classiques et d'applications du Windows Store. Visual Studio évolue parallèlement à Windows.  Dans Visual Studio 2015, les bibliothèques et langages du .NET et C++ bénéficient d'avancées très importantes qui s'appliquent à toutes les versions de Windows.  
  
#### <a name="the-net-framework"></a>.NET Framework  
 Microsoft [!INCLUDE[net_v46](./includes/net-v46-md.md)] offre environ 150 nouvelles API et 50 API mises à jour pour prendre en charge davantage de scénarios. Par exemple, d'autres collections implémentent désormais <xref:System.Collections.Generic.IReadOnlyCollection%601>, ce qui les rend plus faciles à utiliser. Par ailleurs, la technologie ASP.NET 5 mentionnée précédemment offre une plateforme .NET adaptée à la création d'applications cloud modernes.  
  
 Les applications du Windows Store écrites en C# qui ciblent le .NET Framework peuvent à présent tirer parti de .NET Native, qui compile les applications en code natif plutôt qu'en IL. [!INCLUDE[net_v46](./includes/net-v46-md.md)] ajoute également RyuJIT, un compilateur juste-à-temps (JIT) 64 bits.  
  
 Les nouveaux compilateurs C# et VB (« Roslyn ») accélèrent considérablement la compilation et fournissent des API d'analyse de code complètes. Visual Studio 2015 tire parti de Roslyn pour fournir davantage de refactorisations, y compris le changement de nom inline, des analyseurs et des correctifs QFE.  
  
 Les langages C# et Visual Basic comportent tous les deux de nombreuses améliorations mineures dans les domaines du langage de base et de la prise en charge de l'IDE. Additionnées les unes aux autres, ces améliorations rendent votre expérience de codage .NET plus intuitive, plus pratique et plus productive.  
  
 Pour plus d’informations, consultez [What ' s New](http://msdn.microsoft.com/library/1d971dd7-10fc-4692-8dac-30ca308fc0fa) et [Blog .NET](http://blogs.msdn.com/b/dotnet/).  
  
#### <a name="c"></a>C++  
 Visual C++ offre des avancées significatives en matière de conformité au langage C++11/14. De plus, il prend en charge le développement multiplateforme pour appareils mobiles et les fonctions avec capacité de reprise et d'attente (normalisation actuellement prévue dans C++17), et présente des améliorations et des résolutions de bogue dans les implémentations de la bibliothèque Runtime C (CRT) et de la bibliothèque standard C++ (STL), des boîtes de dialogue redimensionnables dans MFC, de nouvelles optimisations du compilateur, de meilleures performances en matière de génération, de nouvelles fonctions de diagnostic et de nouveaux outils de productivité dans l'éditeur de code.  
  
 Pour plus d’informations, consultez [quelles sont les nouveautés de Visual C++](http://msdn.microsoft.com/library/1cc09fad-85a2-43c2-b022-bb99f5fe0ad7) et [Blog Visual C++](http://blogs.msdn.com/b/vcblog/).  
  
## <a name="device-preview-menu-bar"></a>Barre de menus Aperçu de l'appareil  
 Dans les projets de plateforme Windows universelle, la barre de menus Aperçu de l'appareil vous permet de voir comment votre interface utilisateur basée sur XAML sera rendue dans différentes tailles d'écran.  
  
 ![Menu d’aperçu appareil](./ide/media/vs2015-device-preview.png "vs2015_device_preview")  
  
## <a name="visual-studio-graphics-diagnostics"></a>Diagnostics des graphiques Visual Studio  
 Depuis Visual Studio 2013, Diagnostics des graphiques Visual Studio a ajouté de nombreuses nouvelles fonctionnalités, y compris l'analyse des frames, la prise en charge de Windows Phone, la modification et l'application de nuanceur, ainsi que des outils de capture de ligne de commande. La prise en charge du débogage des applications DirectX12 a également été ajoutée. Pour plus d'informations, consultez [Diagnostics des graphiques Visual Studio](./debugger/visual-studio-graphics-diagnostics.md).  
  
## <a name="connect-to-services"></a>Se connecter aux services  
 Visual Studio 2015 facilite de façon considérable la connexion de votre application à des services.  Le nouvel Assistant qui offre la fonctionnalité Ajouter un service connecté configure votre projet, ajoute la prise en charge de l'authentification appropriée, puis télécharge les paquets NuGet nécessaires pour vous aider à démarrer le codage de votre service rapidement et facilement. L'Assistant lié à la fonctionnalité Ajouter un service connecté s'intègre également au nouveau gestionnaire de comptes pour faciliter le travail avec plusieurs comptes d'utilisateur et abonnements. Dans Visual Studio 2015, la prise en charge des services suivants est fournie par défaut (vous devez disposer d'un compte) :  
  
1.  Azure Mobile Services  
  
2.  Azure Storage  
  
3.  Office 365 (messages électroniques, contacts, calendriers, fichiers, utilisateurs et groupes)  
  
4.  Salesforce  
  
 De nouveaux services seront ajoutés sur une base continue. Vous pouvez les découvrir en cliquant sur le lien « Rechercher de nouveaux services » dans l'Assistant.  
  
 ![Boîte de dialogue Services connectés ajouter](./ide/media/vs2015-addconnectedservicedialog.png "VS2015_AddConnectedServiceDialog")  
  
## <a name="design-your-ui"></a>Concevoir votre interface utilisateur  
 L'expérience Blend de conception d'interfaces utilisateur XAML a été considérablement améliorée. Blend a été complètement repensé pour offrir une interface utilisateur plus intuitive, des fonctionnalités d'édition XAML plus puissantes, dont IntelliSense, et une meilleure intégration à Visual Studio. Pour plus d’informations, consultez [XAML de conception dans Visual Studio et Blend pour Visual Studio](./designers/designing-xaml-in-visual-studio.md).  
  
## <a name="cross-platform-debugging-support"></a>Prise en charge du débogage multiplateforme  
 Vous pouvez utiliser Visual Studio pour créer et déboguer des applications mobiles natives qui s'exécutent sur des appareils Windows, iOS et Android. Utilisez l’ [émulateur Visual Studio pour Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx), ou connectez un appareil et déboguez votre code directement dans Visual Studio.  
  
-   **JavaScript / Cordova**. Utilisez [Visual Studio Tools pour Apache Cordova](http://msdn.microsoft.com/library/dn879821\(v=vs.140\).aspx) pour créer des applications natives pour Windows, iOS et Android avec JavaScript.  
  
     [Déboguer votre application](http://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1) dans la bibliothèque MSDN est la description détaillée de la prise en charge de Cordova de débogage Visual Studio.  
  
-   **C# / Xamarin**. Utilisez [Xamarin](http://msdn.microsoft.com/library/dn879698\(v=vs.140\).aspx) pour créer des applications natives pour Windows, iOS et Android dans Visual Studio avec le langage C#.  
  
     Les articles[Debugging](http://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/) (iOS) et [Debug on Device](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debugging_with_xamarin_android/) des [guides du développeur Xamarin](http://developer.xamarin.com/guides) décrivent le débogage.  
  
-   **C++ / Android**. Utilisez les modèles de [Visual C++ pour le développement mobile multiplateforme](http://msdnstage.redmond.corp.microsoft.com/library/dn872463\(v=vs.140\).aspx) , ainsi que les outils tiers, tels que [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html) , pour créer des applications natives pour Windows et Android.  
  
## <a name="debugging-and-diagnostics"></a>Débogage et diagnostics  
 Pour plus d’informations sur les nouvelles fonctionnalités de débogage, consultez [What’s New for the Debugger in Visual Studio 2015](./debugger/what’s-new-for-the-debugger-in-visual-studio-2015.md).  
  
 Pour plus d’informations sur les nouveautés introduite dans les diagnostics, consultez [What ' s New in des outils de profilage](./profiling/what-s-new-in-profiling-tools.md).  
  
 Voici une liste d'outils nouveaux ou améliorés qui effectuent différents types d'analyses et de diagnostics sur votre code :  
  
### <a name="perftips"></a>Conseils sur les performances  
 Les conseils pour les performances indiquent le temps d'exécution des méthodes durant le débogage, ce qui vous permet d'identifier rapidement les goulots d'étranglement, sans avoir à invoquer le profileur. Pour commencer, consultez [Conseils sur les performances : Performance Information at-a-glance while Debugging with Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx)  
  
### <a name="error-list"></a>Liste d'erreurs  
 La liste d'erreurs prend désormais en charge le filtrage sur n'importe quelle colonne. Elle affiche aussi une vue dynamique des erreurs, des avertissements et de l'analyse du code dans l'ensemble de votre solution C# ou Visual Basic, au fur et à mesure que vous tapez, même quand un changement de code produit des milliers d'avertissements. La nouvelle liste d'erreurs est compatible avec les usages existants. Pour plus d'informations, consultez [Error List Window](./ide/reference/error-list-window.md).  
  
### <a name="gpu-usage-tool"></a>Outil Utilisation du GPU  
 L'outil Utilisation du GPU vous aide à collecter et analyser les données sur l'utilisation du GPU dans les applications et jeux DirectX. Il vous aide également à déterminer si les goulots d'étranglement en matière de performances sont dus à l'UC ou au GPU. Pour commencer à utiliser l’outil, consultez ce [billet de blog de l’équipe Visual C++](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx).  
  
## <a name="live-code-analysis-light-bulbs"></a>Analyse de code dynamique (ampoules)  
 Le nouveau compilateur Roslyn pour C# et Visual Basic ne fournit pas seulement des délais de compilation plus rapides. Il permet également des scénarios inédits tels que l'analyse de code dynamique, qui fournit des commentaires et des suggestions, à la fois riches et personnalisables, directement dans l'éditeur de code au fur et à mesure que vous tapez. Dans Visual Studio 2015, des ampoules apparaissent dans la marge de gauche (quand vous utilisez le clavier) ou une info-bulle s'affiche (quand vous passez le curseur de la souris sur une erreur). L'ampoule indique en temps réel que le compilateur (éventuellement à l'aide d'un ensemble de règles personnalisé) a détecté un problème dans votre code et vous suggère une correction. Quand vous voyez une ampoule, cliquez dessus pour obtenir des suggestions d'action.  
  
 ![Les ampoules dans l’éditeur de Code Visual Studio](./ide/media/vs2015-lightbulbs.png "VS2015_LightBulbs")  
  
## <a name="enjoy-these-additional-ide-improvements"></a>Profiter des améliorations supplémentaires de l'IDE  
  
### <a name="synchronized-settings-roaming-settings"></a>Paramètres synchronisés (paramètres d'itinérance)  
 Visual Studio 2013 a introduit les paramètres synchronisés pour certains des paramètres les plus souvent configurés, par exemple l'éditeur de texte, les combinaisons de touches, les thèmes, les polices et couleurs, le démarrage et les alias d'environnement.  Visual Studio 2015 améliore cette expérience en synchronisant davantage de paramètres, et en les synchronisant pour l'ensemble des applications de la famille Visual Studio (par exemple, les versions Professional, Enterprise, Express et Blend). Quand vous vous connectez à Visual Studio 2015 pour la première fois avec le compte utilisé dans Visual Studio 2013, vos paramètres synchronisés sont appliqués à partir de Visual Studio 2013. Vous pouvez également accéder à vos paramètres en tapant « sync » dans **lancement rapide**, ou en accédant à **Outils > Options > environnement > Paramètres synchronisés**.  
  
### <a name="automatic-extension-updates"></a>mises à jour d'extensions automatiques  
 Les extensions Visual Studio installées sont automatiquement mises à jour lorsqu'une nouvelle version est disponible dans la galerie Visual Studio. Consultez [Recherche et utilisation des extensions Visual Studio](./ide/finding-and-using-visual-studio-extensions.md) pour plus d'informations sur la personnalisation des mises à jour d'extensions automatiques.  
  
### <a name="title-case-menus"></a>Menus avec 1re lettre des mots en majuscule  
 Nous vous avons entendus. Les menus de Visual Studio comportent à nouveau la 1re lettre des mots en majuscule, par défaut. Toutefois, si vous aimez le style tout en majuscules, vous pouvez configurer sur Démarrer, ou dans le **Outils > Options > Général** page de propriétés :  
  
 ![Commandes de Menu des principaux cas titre de Visual Studio 2015](./ide/media/vs2015-mainmenu.png "VS2015_MainMenu")  
  
### <a name="high-resolution-images-and-touch-support"></a>Images en haute résolution et prise en charge de l'interface tactile  
 L'IDE de Visual Studio dispose désormais de véritables images en haute définition pour les affichages plus denses (dans les zones comme les menus, les menus contextuels, les barres de commandes de la fenêtre Outil, ainsi que dans certains projets de l'Explorateur de solutions). En outre, sur un écran tactile, dans la fenêtre de l'éditeur de code Visual Studio, vous pouvez maintenant utiliser des actions telles que maintenir appuyé, pincer, appuyer, etc., pour zoomer, faire défiler, sélectionner du texte ou appeler des menus contextuels.  
  
 ![Touch prise en charge dans l’éditeur](./ide/media/vs2015-touchsupport.png "VS2015_TouchSupport")  
  
### <a name="custom-layouts"></a>Dispositions personnalisées  
 Vous pouvez créer, stocker et rendre itinérantes des dispositions de fenêtres personnalisées. Par exemple, vous pouvez définir une disposition favorite à utiliser sur votre ordinateur de bureau, et une autre disposition à utiliser sur un ordinateur portable ou un appareil avec un petit écran. Vous pouvez également préférer une disposition particulière pour un projet d'interface utilisateur, et une autre pour un projet de base de données. Les combinaisons de touches vous permettent de passer rapidement d'une disposition à une autre. Ces dispositions sont accessibles dans toutes les instances de Visual Studio quand vous êtes connecté. Pour plus d'informations, consultez [Créer des dispositions de fenêtres personnalisées](./misc/create-custom-window-layouts.md).  
  
 ![Élément de menu de Visual Studio une disposition personnalisée](./ide/media/vs2015-customlayout.png "VS2015_CustomLayout")  
  
### <a name="notification-hub"></a>Hub de notification  
 L'interface utilisateur du hub de notification a été simplifiée pour faciliter des analyses rapides. Des types de notifications ont été ajoutés, qui concernent notamment des problèmes de performances, des problèmes de rendu et des défaillances. Vous pouvez aussi désormais indiquer à Visual Studio d'arrêter d'afficher une notification. Pour plus d’informations, consultez [Notifications de Visual Studio](./ide/visual-studio-notifications.md).  
  
### <a name="codelens-find-what-happened-to-your-code-enterprise-and-professional-editions-only"></a>CodeLens : découvrez ce qui est arrivé à votre code (éditions Enterprise et Professional uniquement)  
 Ne perdez pas le fil : recherchez des informations relatives à votre code sans quitter l’éditeur. Vous pouvez examiner les modifications et autres éléments de l’historique pour les éléments de travail, bogues, révisions du code, etc. pour le code stocké dans Visual Studio Online (VSO) ou dans Team Foundation Server (TFS).  
  
 Dans Visual Studio Enterprise et Visual Studio Professional, vous pouvez désormais effectuer les opérations suivantes :  
  
-   Obtenir l'historique d'un fichier de code entier dans l'éditeur Visual Studio.  
  
     ![CodeLens : obtenir des détails sur le fichier de code](./ide/media/codelensfilelevel.png "CodeLensFileLevel")  
  
-   Consulter un graphique indiquant les personnes qui ont modifié votre code. Cette fonctionnalité vous permet de découvrir des modèles dans les modifications effectuées par votre équipe, et d’en évaluer l’impact.  
  
     ![CodeLens : voir l’historique des modifications du code sous forme de graphique](./ide/media/codelens.png "CodeLens")  
  
-   Afficher rapidement la date de dernière modification de votre code.  
  
-   Rechercher les modifications apportées dans d’autres branches qui affectent votre code.  
  
 Consultez [CodeLens](./ide/find-code-changes-and-other-history-with-codelens.md).  
  
### <a name="design-and-modeling-tools-enterprise-edition-only"></a>Outils de conception et de modélisation (Enterprise Edition uniquement)  
 **Cartes de code et des graphiques de dépendance**  
  
 Dans Visual Studio Enterprise, quand vous voulez comprendre les dépendances spécifiques dans votre code, vous pouvez les visualiser en créant des cartes de code. Vous pouvez alors parcourir ces relations à l'aide de la carte, laquelle est affichée en regard de votre code. Les cartes de code peuvent aussi vous aider à savoir où vous vous trouvez dans le code pendant que vous travaillez ou déboguez le code. Vous passerez donc moins de temps à lire le code, tout en approfondissant vos connaissances sur sa conception.  
  
 Dans cette version, nous avons simplifié l'utilisation des liens et des menus contextuels pour les éléments de code en regroupant les commandes dans des sections en rapport avec la sélection, la modification, la gestion des groupes et la modification de la disposition du contenu des groupes. Notez également que les projets de test sont affichés dans un style différent des autres projets et que nous avons mis à jour les icônes des éléments sur la carte avec des versions plus appropriées.  
  
 ![Afficher les éléments sélectionnés sur une nouvelle carte de code](./ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")  
  
 Voici quelques autres améliorations qui ont été apportées :  
  
-   **Amélioration des diagrammes de haut en bas**. Pour les solutions Visual Studio de taille moyenne à grande, vous pouvez désormais utiliser un menu Architecture simplifié pour obtenir des cartes de code plus utiles pour votre solution. Les assemblys de votre solution sont regroupés par dossier de solution, ce qui vous permet de les voir dans le contexte et de tirer parti de l'effort que vous avez fourni en termes de structuration de la solution. Vous voyez immédiatement les projets et les références d'assemblys, puis les types de liens apparaissent. En outre, les assemblys externes à votre solution sont regroupés de manière plus compacte.  
  
-   **Les projets de test ont un style différent et ils peuvent être filtrés**. Vous pouvez désormais identifier plus facilement et plus rapidement les projets de test sur la carte, car ils ont un style différent. Vous pouvez aussi les filtrer pour pouvoir vous concentrer sur le code actif de l'application.  
  
-   **Simplification des liens de dépendance externe**. Les liens de dépendance ne représentent plus l'héritage de System.Object, System.ValueType, System.Enum et System.Delegate, ce qui facilite l'identification des dépendances externes dans votre carte de code.  
  
-   **L'exploration des liens de dépendance tiennent compte des filtres**. Vous obtenez un diagramme clair et utile qui, lorsqu'il est développé, vous permet de comprendre les contributions associées à un lien de dépendance. Le diagramme est moins encombré et il tient compte des options de filtrage des liens que vous avez sélectionnées.  
  
-   **Les éléments de code sont ajoutés à une carte de code avec leur contexte**. Étant donné que les diagrammes sont maintenant affichés avec leur contexte (jusqu'au dossier d'assembly et de solution sur lequel vous pouvez appliquer un filtre, si nécessaire), vous obtenez des diagrammes plus utiles quand vous faites glisser-déplacer des éléments de code à partir de l'Explorateur de solutions, de l'Affichage de classes ou de l'Explorateur d'objets, ou lors de la sélection d'éléments dans l'Explorateur de solutions et du choix de l'option Afficher sur la carte de code.  
  
-   **Génération plus rapide de cartes de code réactives**. Les opérations de glisser-déplacer produisent un résultat immédiat et les liens entre les nœuds sont créés beaucoup plus rapidement, sans affecter les opérations ultérieures initiées par l'utilisateur, telles que le développement d'un nœud ou la demande de nœuds supplémentaires. Quand vous créez des cartes de code sans générer la solution, tous les cas extrêmes, par exemple lorsque les assemblys ne sont pas générés, sont désormais traités.  
  
-   **Ignorer la régénération de votre solution.** Fournit de meilleures performances lors de la création et de la modification des diagrammes.  
  
-   **Filtrage des groupes et des nœuds d'éléments de code**. Vous pouvez rapidement mettre en ordre vos cartes en affichant ou en masquant des éléments de code en fonction de leur catégorie, ainsi qu'en regroupant les éléments de code par dossier de solution, assembly, espace de noms, dossier de projet et type.  
  
-   **Filtrage des relations pour faciliter la lecture des diagrammes**. Le filtrage des liens s'applique désormais également aux liens intergroupes, ce qui rend l'utilisation de la fenêtre de filtre moins gênante qu'elle ne l'était dans les versions précédentes.  
  
-   **Création de diagrammes à partir de l'Affichage de classes et de l'Explorateur d'objets**. Glissez-déplacez des fichiers et des assemblys sur une carte nouvelle ou existante à partir des fenêtres Affichage de classes et Explorateur d'objets.  
  
 Consultez [Map dependencies across your solutions](./modeling/map-dependencies-across-your-solutions.md).  
  
 **Autres modifications de conception et de modélisation dans cette version :**  
  
-   **Diagrammes de couche**. Mettez à jour ces diagrammes à l'aide de l'Affichage de classes et de l'Explorateur d'objets. Pour répondre aux exigences de conception de logiciel, utilisez des diagrammes de couche pour décrire les dépendances souhaitées pour votre logiciel. Assurez la cohérence du code avec cette conception en recherchant le code qui ne respecte pas ces contraintes et en validant le code ultérieur avec cette ligne de base.  
  
-   **Diagrammes UML**. Vous ne pouvez plus créer des diagrammes de classes UML et des diagrammes de séquence à partir du code. Pour créer ces diagrammes, vous devez à présent utiliser de nouveaux éléments UML.  
  
-   **Navigateur de l'architecture**. Vous ne pouvez plus utiliser le Navigateur de l'architecture pour créer des diagrammes. Mais vous pouvez toujours utiliser l'Explorateur de solutions.  
  
## <a name="visual-studio-extensibility-tools"></a>Outils d'extensibilité de Visual Studio  
 Il n'a jamais été aussi facile d'installer les outils d'extensibilité Visual Studio (Kit de développement logiciel Visual Studio et modèles), car ils sont désormais inclus en tant que composant facultatif lors de l'installation.  Les outils d'extensibilité permettent aux développeurs d'écrire des extensions pour personnaliser et ajouter des fonctionnalités à Visual Studio. Pour plus d'informations sur l'extensibilité de Visual Studio, consultez [Kit de développement logiciel Visual Studio](./extensibility/visual-studio-sdk.md)  
  
 Si vous souhaitez inclure les outils d'extensibilité dans votre installation personnalisée, vous les trouverez sous **Fonctionnalités / Outils courants / Outils d'extensibilité de Visual Studio**.  Vous pouvez également installer les outils d'extensibilité ultérieurement en ouvrant la boîte de dialogue **Nouveau projet** et en sélectionnant l'élément **Installer les outils d'extensibilité Visual Studio** sous **Visual C# / Extensibilité**.  
  
## <a name="please-give-feedback"></a>Envoyer des commentaires  
 Vous vous demandez peut-être quel est l'intérêt d'envoyer des commentaires à l'équipe Visual Studio. C'est simple : nous prenons très au sérieux les commentaires de nos clients. En fait, nous passons en revue tous les commentaires qui sont entrés dans le système, et ceux-ci influencent bon nombre de nos décisions.  
  
### <a name="send-a-smile"></a>Envoyer un sourire  
 En indiquant les fonctionnalités que vous aimez, vous nous aidez à mieux comprendre ce qui comble voire dépasse vos attentes. Au moment de concevoir et d'implémenter de nouvelles fonctionnalités, nous utilisons ces données pour guider nos décisions en matière de conception. Donc, si vous aimez une fonctionnalité particulière dans Visual Studio, signalez-la. C'est facile et vous pouvez le faire directement dans l'IDE.  
  
 Cliquez simplement sur l'émoticône jaune dans la barre de titre, dites-nous ce qui vous plaît, puis cliquez sur le bouton **Envoyer un sourire** .  
  
 C'est tout ! Votre commentaire est alors transmis à l'équipe concernée qui peut s'en servir pour améliorer encore plus la fonctionnalité.  
  
### <a name="send-a-frown"></a>Envoyer un smiley mécontent  
 Il est important pour nous d'identifier les zones du produit à améliorer. Cela nous permet de mieux gérer notre backlog et de nous pencher en priorité sur ce qui importe le plus à nos clients. Si quelque chose vous importune, utilisez la fonctionnalité **Envoyer un smiley mécontent** pour nous en faire part directement dans l'IDE. La procédure à suivre est très simple :  
  
 Cliquez sur l'émoticône jaune dans la barre de titre, puis cliquez sur **Envoyer un smiley mécontent**. Indiquez ce qui vous dérange, puis cliquez sur le bouton Envoyer un smiley mécontent. Pour plus d’informations, consultez [Nous contacter](./ide/talk-to-us.md).  
  
### <a name="report-crashes-hangs-and-performance-issues"></a>Signaler les accidents, blocages et problèmes de performance  
 Parfois, une note rapide dans un smiley mécontent ne suffit pas à rendre pleinement compte d'un problème. Si vous vous heurtez à un blocage, un incident ou un problème de performance, vous pouvez facilement partager les étapes de reproduction, les vidages sur incident et les fichiers de trace dans la boîte de dialogue qui apparaît après l'envoi d'un smiley mécontent.  
  
 Tout d'abord, envoyez un smiley mécontent comme décrit ci-dessus. Ensuite, dans la boîte de dialogue qui s'affiche, vous pouvez marquer vos commentaires à l'aide de l'une des étiquettes par défaut ou créer votre propre étiquette. Les étiquettes nous aident à transmettre vos commentaires à la bonne équipe. Dans la liste déroulante **Choisir une catégorie** , sélectionnez l'option correspondant au problème que vous rencontrez, puis suivez les étapes pour reproduire le problème. Des étapes détaillées sur la façon d'utiliser Visual Studio pour signaler des commentaires sont également disponibles. Pour plus d’informations, consultez [Visual Studio envoyer un sourire d’Instructions](http://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b).  
  
### <a name="track-your-issue-in-connect"></a>Effectuer le suivi d'un problème dans Connect  
 Si vous voulez savoir où en est la prise en compte de vos commentaires sur Visual Studio 2015, accédez à la page [Connect](http://connect.microsoft.com/) , puis signalez-y le bogue. Une fois le bogue signalé, vous pouvez revenir à la page Connect pour faire le suivi de l'état du bogue.  
  
## <a name="see-also"></a>Voir aussi  
* [Générer des applications multiplateformes avec Apache Cordova](http://msdn.microsoft.com/library/34d3c1be-22b3-4812-97fb-10b4e8ad2134)   
* [Générer des applications Xamarin avec une interface utilisateur native dans Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)   
* [Générer des applications interplateformes avec Visual C++](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md) 
* [Générer des tests unitaires pour votre code avec IntelliTest](./test/generate-unit-tests-for-your-code-with-intellitest.md)   
* [Utiliser plusieurs comptes d’utilisateur](./ide/work-with-multiple-user-accounts.md)   
* [Créer des dispositions de fenêtres personnalisées](./misc/create-custom-window-layouts.md)   
* [Effectuer des actions rapides avec des ampoules](./ide/perform-quick-actions-with-light-bulbs.md)   
* [Quelles sont les nouveautés d’Application Lifecycle Management dans Visual Studio 2015](http://msdn.microsoft.com/en-us/54b98a53-6083-4303-869a-8063d8fae938)
* [Nouveautés de Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)
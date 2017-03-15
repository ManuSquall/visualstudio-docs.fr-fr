---
title: "R&#233;solution des probl&#232;mes des exceptions&#160;: erreurs de build Cordova | Microsoft Docs"
ms.custom: ""
ms.date: "11/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLD102"
  - "BLD10205"
  - "BLD301"
  - "BLD401"
  - "BLDErr_Build_NodeMissing"
  - "BLDErr_BLD_Win8Required"
ms.assetid: 781c09e3-0704-4b30-9230-036cbdb2dff9
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
---
# R&#233;solution des probl&#232;mes des exceptions&#160;: erreurs de build Cordova
Cette rubrique décrit certains des messages d’erreur les plus courants qui peuvent s’afficher quand vous utilisez Visual Studio Tools pour Apache Cordova.  
  
-   [MSBUILD : erreur de build Cordova BLD102 : aucun fichier ou répertoire ’config.xml’](#BLD102)  
  
-   [MSBUILD : erreur de build Cordova BLD301 : un agent de build iOS distant n’a pas été configuré](#BLD301)  
  
-   [MSBUILD : erreur de build Cordova BLD401 : module &lt;nom_module&gt; introuvable](#BLD401)  
  
-   [MSBUILD : erreur de build Cordova BLD10205 : installez la cible Android](#BLD10205)  
  
-   [Impossible de déterminer le chemin BLDErr_Build_NodeMissing vers l’exécutable Node.js.](#BLDErr_Build_NodeMissing)  
  
-   [BLDErr_Build_Win8Required](#BLDErr_Build_Win8Required)  
  
 Si vous avez besoin d’une aide plus générale pour le dépannage des erreurs dans votre application Cordova, consultez [Resolving build errors \(Résolution des erreurs de build\)](https://taco.visualstudio.com/en-us/docs/resolving-build-errors/).  
  
##  <a name="BLD102"></a> MSBUILD : erreur de build Cordova BLD102 : aucun fichier ou répertoire ’config.xml’  
 Si cette erreur s’affiche, vérifiez que votre projet inclut un fichier config.xml à la racine du projet et que votre projet se trouve sur l’ordinateur local et non sur un partage réseau.  
  
 Pour plus d’informations, consultez ce [billet StackOverflow](http://stackoverflow.com/questions/27134007/new-cordova-project-gives-the-error-bld00102-no-such-file-or-directory-confi).  
  
##  <a name="BLD301"></a> MSBUILD : erreur de build Cordova BLD301 : un agent de build iOS distant n’a pas été configuré  
 La chaîne d’erreur complète est la suivante :  
  
-   MSBUILD : erreur de build Cordova BLD301 : un agent de build iOS distant n’a pas été configuré. Configurez\-en un dans Outils \> Options \> Outils pour Apache Cordova \> Configuration de l’agent distant. Pour obtenir des informations et d’autres choix possibles, consultez http:\/\/go.microsoft.com\/fwlink\/?LinkID\=511904  
  
 Pour plus d’informations sur l’installation et la configuration de l’agent de build distant pour iOS, consultez le [guide d’installation iOS](http://taco.visualstudio.com/en-us/docs/ios-guide/).  
  
##  <a name="BLD401"></a> MSBUILD : erreur de build Cordova BLD401 : module \<nom\_module\> introuvable  
 La chaîne d’erreur complète est la suivante :  
  
-   MSBUILD : erreur de build Cordova BLD401 : Erreur : BLD00401 : module \<nom\_module\> introuvable. Accédez à Outils \-\-\> Options \-\-\> Outils pour Apache Cordova \-\-\> Outils Cordova \-\-\> Effacer le cache Cordova, puis tentez de réexécuter la génération.  
  
 Vous devrez peut\-être effacer le cache et réinstaller vs\-tac. Pour plus d’informations, consultez [Réinstaller vs\-tac](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#vstac).  
  
 Après avoir effacé le cache, supprimez le dossier de plateformes dans le projet. Ensuite, réessayez de générer.  
  
##  <a name="BLD10205"></a> MSBUILD : erreur de build Cordova BLD10205 : installez la cible Android  
 Si cette erreur s’affiche, vérifiez que vous installez les dépendances requises pour l’appareil cible sélectionné à l’aide du Gestionnaire du Kit de développement logiciel \(SDK\) Android \(SDK Manager.exe\).  
  
 Pour plus d’informations sur le niveau requis de l’API et d’autres composants du Kit de développement logiciel \(SDK\) Android, consultez [Installer manuellement des dépendances](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#ThirdParty).  
  
 Vous devez également vérifier l’emplacement utilisé par Visual Studio pour rechercher le Kit de développement logiciel \(SDK\) Android. Pour ce faire, consultez [Remplacer des variables d’environnement système](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#env-var).  
  
 Pour plus d’informations sur l’installation des composants appropriés pour utiliser les outils, consultez [Outils tiers](http://taco.visualstudio.com/en-us/docs/install-vs-tools-apache-cordova#choose).  
  
##  <a name="BLDErr_Build_NodeMissing"></a> Impossible de déterminer le chemin BLDErr\_Build\_NodeMissing vers l’exécutable Node.js.  
 Si Node.js a été installé à un emplacement non défini par défaut, Visual Studio peut ne pas le trouver. Réinstallez Node.js à l’emplacement par défaut. Pour plus d’informations, consultez ce [billet StackOverflow](http://stackoverflow.com/questions/32203992/vs2015-cordova-apps-blderr-build-nodemissing) et cet article sur la [mise à jour en toute sécurité de Node.js](http://taco.visualstudio.com/en-us/docs/change-node-version/).  
  
##  <a name="BLDErr_Build_Win8Required"></a> BLDErr\_Build\_Win8Required  
 Windows 8.1 est requis pour cibler Windows dans une application créée à l’aide de Visual Studio Tools pour Apache Cordova.
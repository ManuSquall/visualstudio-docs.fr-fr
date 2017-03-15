---
title: "D&#233;bogage distant ASP.NET sur un ordinateur distant IIS&#160;7.5 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;bogage distant ASP.NET sur un ordinateur distant IIS&#160;7.5
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez déployer une application web ASP.NET sur un ordinateur Windows Server 2008 R2 avec IIS 7.5 et le configurer pour le débogage distant. Les instructions suivantes expliquent comment installer et configurer une application Visual Studio 2015 MVC 4.5.2.  
  
## Créer l’application sur l’ordinateur Visual Studio  
  
1.  Créez une application ASP.NET MVC. \(**Fichier \/ Nouveau \/ Projet**, puis sélectionnez **Visual C\# \/ Web \/ Application web ASP.NET**. Dans la section des modèles **ASP.NET 4.5.2**, sélectionnez **MVC**. Annulez la page **Configurer l’application web Microsoft Azure**. \) et nommez\-la **MyMVC**.  
  
2.  Ouvrez le fichier HomeController.cs et définissez un point d’arrêt dans la méthode `About()`.  
  
3.  Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet et sélectionnez **Publier**.  
  
4.  Pour **Sélectionner une cible de publication**, sélectionnez **Personnalisée** et nommez le profil **MyMVC**. Cliquez sur **Suivant**.  
  
5.  Sous l’onglet **Connexion**, définissez le champ **Méthode de publication** sur **Système de fichiers** et le champ **Emplacement cible** sur un répertoire local. Cliquez sur **Suivant**.  
  
6.  Définissez la configuration en **Debug**. Cliquez sur **Publier**.  
  
     L’application doit être publiée dans le répertoire local.  
  
## Déployer l’application sur l’ordinateur distant Windows Server  
 Cette section suppose qu’IIS est déjà activé sur l’ordinateur Windows Server 2008 R2.  
  
1.  Installez ASP.NET :  
  
     **C:\\Windows\\Microsoft.NET\\Framework\(64\)\\v4.0.30319\\aspnet\_regiis.exe \-ir**  
  
2.  Copiez le répertoire de projet ASP.NET de l’ordinateur Visual Studio dans un répertoire local \(que nous appelons **C:\\Publish**\) sur l’ordinateur Windows Server.  
  
3.  Assurez\-vous que le fichier web.config indique la version correcte du .NET Framework.  La version du .NET Framework installée par défaut sur cet ordinateur est 4.0.30319, mais nous avons créé une version ASP.NET 4.5.2. Si cette version n’est pas installée sur l’ordinateur Windows Server, vous devez modifier la version :  
  
    ```xml  
    <system.web> <authentication mode="None" /> <compilation debug="true" targetFramework="4.0.30319" /> <httpRuntime targetFramework="4.0.30319" /> </system.web>  
  
    ```  
  
4.  Ouvrez le **Gestionnaire des services Internet \(IIS\)**.et accédez à **Sites**.  
  
5.  Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.  
  
6.  Définissez le champ **Alias** sur **MyMVC** et le champ Pool d’applications sur **ASP.NET v4.0**. Définissez le **Chemin d’accès physique** sur **C:\\Publish** \(où vous avez copié le répertoire de projet ASP.NET\).  
  
7.  Pour tester le déploiement, cliquez avec le bouton droit sur **Site web par défaut** et sélectionnez **Parcourir**. La page web doit s’afficher.  
  
## Installer le débogueur distant sur l’ordinateur Windows Server  
 Pour savoir comment télécharger le débogueur distant, consultez [Débogage distant](../debugger/remote-debugging.md).  
  
 Pour effectuer un débogage distant d’applications ASP.NET, vous pouvez démarrer le débogueur distant en tant que service ou exécuter l’application du débogueur distant en tant qu’administrateur. Pour plus d’informations l’exécution du débogueur distant en tant que service, consultez [Débogage distant](../debugger/remote-debugging.md).  
  
## Attachement à l’application ASP.NET à partir de l’ordinateur Visual Studio  
  
-   Sur l’ordinateur Visual Studio, ouvrez la solution **MyMVC**.  
  
-   Dans Visual Studio, cliquez sur **Déboguer \/ Attacher au processus**.  
  
-   Définissez le champ Qualificateur sur **\<nom\_ordinateur\_distant \>:4020**.  
  
-   Des processus doivent s’afficher dans la fenêtre **Processus disponibles**.  
  
-   Cochez **Afficher les processus de tous les utilisateurs**.  
  
-   Recherchez **w3wp.exe** et cliquez sur **Attacher**.  
  
-   Ouvrez le site web de l’ordinateur distant. Dans un navigateur, accédez à **http:\/\/\<nom\_ordinateur\_distant\>**.  
  
-   La page web ASP.NET doit s’afficher. Cliquez sur **À propos de**.  
  
     Le point d’arrêt doit être atteint dans Visual Studio.
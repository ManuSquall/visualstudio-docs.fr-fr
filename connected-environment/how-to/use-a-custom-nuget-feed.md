---
title: Guide pratique pour utiliser un flux NuGet personnalisé dans un environnement connecté | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 03/27/2018
ms.topic: conceptual
description: Utilisez un flux NuGet personnalisé pour consulter et utiliser les packages NuGet dans un environnement connecté.
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, conteneurs
manager: douge
ms.openlocfilehash: 1c4c0c53b81f29436bb7110395981071411fd6b2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
#  <a name="use-a-custom-nuget-feed-in-a-connected-environment"></a>Utiliser un flux NuGet personnalisé dans un environnement connecté

Le flux NuGet représente un moyen pratique d’inclure des sources de package dans un projet. Connected Environment aura besoin d’un accès à ce flux pour que les dépendances soient correctement installées dans le conteneur Docker.

Pour configurer un flux NuGet :
1. Ajouter une [référence de package](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files) dans le fichier `*.csproj` sous le nœud `PackageReference`.

   ```xml
   <ItemGroup>
       <!-- ... -->
       <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0" />
       <!-- ... -->
   </ItemGroup>
   ```

2. Créez un fichier [NuGet.Config](https://docs.microsoft.com/en-us/nuget/reference/nuget-config-file) dans le dossier du projet.
     * Utilisez la section `packageSources` pour faire référence à l’emplacement de votre flux NuGet. Important : Le flux NuGet doit être accessible publiquement.
     * Utilisez la section `packageSourceCredentials` pour configurer les identifiants (nom d’utilisateur et mot de passe). 

   ```xml
   <packageSources>
       <add key="Contoso" value="https://contoso.com/packages/" />
   </packageSources>

   <packageSourceCredentials>
       <Contoso>
           <add key="Username" value="user@contoso.com" />
           <add key="ClearTextPassword" value="33f!!lloppa" />
       </Contoso>
   </packageSourceCredentials>
   ```

3. Si vous utilisez le contrôle de code source :
    - Référencez `NuGet.Config` dans votre fichier `.gitignore` pour éviter de valider accidentellement des informations d’identification dans votre référentiel source.
    - Ouvrez le fichier `vsce.yaml` dans votre projet, recherchez la section `build` et insérez l’extrait de code suivant pour que le fichier `NuGet.Config` soit synchronisé dans Azure et ainsi utilisé pendant le processus de génération de l’image conteneur. (Par défaut, Connected Environment ne synchronise pas les fichiers qui correspondent aux règles `.gitignore` et `.dockerignore`.)

        ```yaml
        build:
        useGitIgnore: true
        ignore:
        - “!NuGet.Config”
        ```


## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez suivi les étapes ci-dessus, la prochaine fois que vous exécuterez `vsce up` (ou que vous appuierez sur `F5` dans VSCode ou Visual Studio), Connected Environment synchronisera le fichier `NuGet.Config` sur Azure, ce qui sera ensuite utilisé par `dotnet restore` pour installer les dépendances du package dans le conteneur.


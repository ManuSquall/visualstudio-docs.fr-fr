---
title: Propriétés de build des outils de conteneur Visual Studio
author: ghogen
description: Vue d’ensemble du processus de génération des outils de conteneur
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 427a70d9bc4f6ef326ffb16e7d26df9d8fae2365
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283201"
---
# <a name="container-tools-build-properties"></a>Propriétés de build des outils de conteneur

Vous pouvez personnaliser la façon dont Visual Studio génère vos projets de conteneur en définissant les propriétés utilisées par MSBuild pour générer votre projet. Par exemple, vous pouvez modifier le nom du fichier dockerfile, spécifier des balises et des étiquettes pour vos images, fournir des arguments supplémentaires passés aux commandes de l’ancrage et contrôler si Visual Studio effectue certaines optimisations de performances telles que la génération en dehors de l’environnement de conteneur. Vous pouvez également définir des propriétés de débogage telles que le nom de l’exécutable à lancer et les arguments de ligne de commande à fournir.

Pour définir la valeur d’une propriété, modifiez le fichier projet. Par exemple, supposons que votre fichier dockerfile soit nommé *MyDockerfile*. Vous pouvez définir la `DockerfileFile` propriété dans le fichier projet comme suit.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Vous pouvez ajouter le paramètre de propriété à un `PropertyGroup` élément existant, ou s’il n’y en a pas, créer un nouvel `PropertyGroup` élément.

Le tableau suivant présente les propriétés MSBuild disponibles pour les projets de conteneur. La version du package NuGet s’applique à [Microsoft. VisualStudio. Azure. Containers. Tools. targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Nom de la propriété | Description | Valeur par défaut  | Version de package NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Contrôle si l’optimisation « génération sur hôte » (débogage « mode rapide ») est activée.  Les valeurs autorisées sont **rapide** et **normale**. | Rapide |1.0.1872750 ou plus récent|
| ContainerVsDbgPath | Chemin d’accès du débogueur VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 ou plus récent|
| DockerDebuggeeArguments | Lors du débogage, le débogueur est invité à passer ces arguments à l’exécutable lancé. | Non applicable aux projets de .NET Framework ASP.NET |1.7.8 ou plus récent|
| DockerDebuggeeProgram | Lors du débogage, le débogueur est invité à lancer ce fichier exécutable. | Pour les projets .NET Core : DotNet, ASP.NET .NET Framework Projects : non applicable (IIS est toujours utilisé) |1.7.8 ou plus récent|
| DockerDebuggeeKillProgram | Cette commande permet de terminer le processus en cours d’exécution dans un conteneur. | Non applicable aux projets de .NET Framework ASP.NET |1.7.8 ou plus récent|
| DockerDebuggeeWorkingDirectory | Lors du débogage, le débogueur est invité à utiliser ce chemin d’accès comme répertoire de travail. | C:\app (Windows) ou/App (Linux) |1.7.8 ou plus récent|
| DockerDefaultTargetOS | Le système d’exploitation cible par défaut utilisé lors de la génération de l’image de l’ancrage. | Défini par Visual Studio. |1.0.1985401 ou plus récent|
| DockerImageLabels | Ensemble d’étiquettes par défaut appliqué à l’image de l’ancrage. | com. Microsoft. created-by = Visual-Studio ; com. Microsoft. Visual-Studio. Project-Name = $ (MSBuildProjectName) |1.5.4 ou plus récent|
| DockerFastModeProjectMountDirectory|En **mode rapide**, cette propriété contrôle l’emplacement où le répertoire de sortie du projet est monté en volume dans le conteneur en cours d’exécution.|C:\app (Windows) ou/App (Linux)|1.9.2 ou plus récent|
| DockerfileBuildArguments | Arguments supplémentaires passés à la commande de génération de l' [amarrage](https://docs.docker.com/engine/reference/commandline/build/) . | Non applicable. |1.0.1872750 ou plus récent|
| DockerfileContext | Contexte par défaut utilisé lors de la génération de l’image de l’ancrage, en tant que chemin d’accès relatif au fichier dockerfile. | Défini par Visual Studio. |1.0.1872750 ou plus récent|
| DockerfileFastModeStage | Étape fichier dockerfile (cible) à utiliser lors de la génération de l’image en mode débogage. | Première étape trouvée dans le fichier dockerfile (base) |
| DockerfileFile | Décrit le fichier dockerfile par défaut qui sera utilisé pour générer/exécuter le conteneur pour le projet. Il peut également s’agir d’un chemin d’accès. | Dockerfile |1.0.1872750 ou plus récent|
| DockerfileRunArguments | Arguments supplémentaires passés à la commande d’exécution de la [station d’accueil](https://docs.docker.com/engine/reference/commandline/run/) . | Non applicable. |1.0.1872750 ou plus récent|
| DockerfileRunEnvironmentFiles | Liste délimitée par des points-virgules des fichiers d’environnement appliqués lors de l’exécution de l’amarrage. | Non applicable. |1.0.1872750 ou plus récent|
| DockerfileTag | Balise qui sera utilisée lors de la génération de l’image de l’ancrage. Lors du débogage, un «  :d ev » est ajouté à la balise. | Nom de l’assembly après la suppression des caractères non alphanumériques avec les règles suivantes : <br/> Si la balise résultante est de type numeric, alors « image » est insérée en tant que préfixe (par exemple, image2314) <br/> Si la balise résultante est une chaîne vide, l’expression « image » est utilisée en tant que balise. |1.0.1872750 ou plus récent|

## <a name="example"></a>Exemple

Le fichier projet suivant présente des exemples de certains de ces paramètres.

```xml
 <Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UserSecretsId>feae72bf-2368-4487-b6c6-546c19338cb1</UserSecretsId>
    <DockerDefaultTargetOS>Linux</DockerDefaultTargetOS>
    <!-- In CI/CD scenarios, you might need to change the context. By default, Visual Studio uses the
         folder above the Dockerfile. The path is relative to the Dockerfile, so here the context is
         set to the same folder as the Dockerfile. -->
    <DockerfileContext>.</DockerfileContext>
    <!-- Set `docker run` arguments to mount a volume -->
    <DockerfileRunArguments>-v $(pwd)/host-folder:/container-folder:ro</DockerfileRunArguments>
    <!-- Set `docker build` arguments to add a custom tag -->
    <DockerfileBuildArguments>-t contoso/front-end:v2.0</DockerfileBuildArguments>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.VisualStudio.Azure.Containers.Tools.Targets" Version="1.10.6" />
  </ItemGroup>

</Project>
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les propriétés MSBuild en général, consultez [propriétés MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Voir aussi

[Docker Compose les propriétés de build](docker-compose-properties.md)

[Paramètres de lancement des outils de conteneur](container-launch-settings.md)

[Propriétés réservées et connues de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)

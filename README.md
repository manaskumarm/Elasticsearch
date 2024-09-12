## Elasticsearch

Elasticsearch is a distributed search and analytics engine, scalable data store and vector database optimized for speed and relevance on production-scale workloads. Elasticsearch is the foundation of Elastic’s open Stack platform. Search in near real-time over massive datasets, perform vector searches, integrate with generative AI applications, and much more.

![image](https://github.com/user-attachments/assets/e30d85b3-372c-448c-97aa-7340f92852d8)

# Code(Elasticsearch)
Integrating Elasticsearch with a .NET Core application for text search involves several steps, from setting up Elasticsearch to implementing the code for indexing and searching records. Below is a detailed guide to help you achieve this integration.
Prerequisites

1.	Elasticsearch Setup: Ensure that Elasticsearch is installed and running on your machine or server. You can download Elasticsearch from Elasticsearch Downloads and follow the installation instructions.
   
2.	.NET Core SDK: Ensure that you have the .NET Core SDK installed on your machine.
Step 1: Install NuGet Packages

First, you need to install the Elasticsearch client for .NET. The most commonly used client is NEST (part of the Elasticsearch.NET package).
In your .NET Core project, install the following NuGet package:

dotnet add package NEST --version <latest_version>
Replace <latest_version> with the latest version available.

Step 2: Set Up Elasticsearch Client
In your .NET Core application, configure the Elasticsearch client to connect to your Elasticsearch instance. You can do this in your Startup.cs or in a dedicated service.

using Nest;
using Microsoft.Extensions.DependencyInjection;

public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Configure the connection to Elasticsearch
        var settings = new ConnectionSettings(new Uri("http://localhost:9200"))
                       .DefaultIndex("myindex"); // Default index name
        
        var client = new ElasticClient(settings);

        // Register the client as a singleton service
        services.AddSingleton<IElasticClient>(client);

        services.AddControllers();
    }
}
Replace "http://localhost:9200" with your Elasticsearch instance's URL.


# Summary

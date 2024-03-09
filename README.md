# Description
Minikube API Server

## Using proxy. Activate API swagger

The easiest way to access the Kubernetes API with when running minikube is to use

```
kubectl proxy --port=8080
```

You can then access the API with

```
curl http://localhost:8080/api/
```

This also allows you to browse the API in your browser. Start minikube using
```
minikube start --extra-config=apiserver.Features.EnableSwaggerUI=true
```

then start kubectl proxy, and navigate to http://localhost:8080/swagger-ui/ 

## Using curl directly

Get all namespaces from kubernetes server. You must use the the ca certificate and client key certificates created by minikube when star the first time like this:

```
curl --cacert ~/.minikube/ca.crt --cert ~/.minikube/profiles/minikube/client.crt --key ~/.minikube/profiles/minikube/client.key https://127.0.0.1:32769/api/v1/namespaces
{
  "kind": "NamespaceList",
  "apiVersion": "v1",
  "metadata": {
    "resourceVersion": "9097"
  },
  "items": [
    {
      "metadata": {
        "name": "default",
        "uid": "e20cb1b1-9382-46f0-898f-1a952ea7125a",
        "resourceVersion": "37",
        "creationTimestamp": "2024-03-09T09:59:41Z",
        "labels": {
          "kubernetes.io/metadata.name": "default"
        },
        "managedFields": [
          {
            "manager": "kube-apiserver",
            "operation": "Update",
            "apiVersion": "v1",
            "time": "2024-03-09T09:59:41Z",
            "fieldsType": "FieldsV1",
            "fieldsV1": {
              "f:metadata": {
                "f:labels": {
                  ".": {},
                  "f:kubernetes.io/metadata.name": {}
                }
              }
            }
          }
        ]
      },
      "spec": {
        "finalizers": [
          "kubernetes"
        ]
      },
      "status": {
        "phase": "Active"
      }
    },
    {
      "metadata": {
        "name": "kube-node-lease",
        "uid": "4903039a-8e84-4500-9bcb-e5efcae92cb7",
        "resourceVersion": "35",
        "creationTimestamp": "2024-03-09T09:59:41Z",
        "labels": {
          "kubernetes.io/metadata.name": "kube-node-lease"
        },
        "managedFields": [
          {
            "manager": "kube-apiserver",
            "operation": "Update",
            "apiVersion": "v1",
            "time": "2024-03-09T09:59:41Z",
            "fieldsType": "FieldsV1",
            "fieldsV1": {
              "f:metadata": {
                "f:labels": {
                  ".": {},
                  "f:kubernetes.io/metadata.name": {}
                }
              }
            }
          }
        ]
      },
      "spec": {
        "finalizers": [
          "kubernetes"
        ]
      },
      "status": {
        "phase": "Active"
      }
    },
    {
      "metadata": {
        "name": "kube-public",
        "uid": "8693fda7-11bf-4fc8-8ac3-64245c66ee20",
        "resourceVersion": "18",
        "creationTimestamp": "2024-03-09T09:59:41Z",
        "labels": {
          "kubernetes.io/metadata.name": "kube-public"
        },
        "managedFields": [
          {
            "manager": "kube-apiserver",
            "operation": "Update",
            "apiVersion": "v1",
            "time": "2024-03-09T09:59:41Z",
            "fieldsType": "FieldsV1",
            "fieldsV1": {
              "f:metadata": {
                "f:labels": {
                  ".": {},
                  "f:kubernetes.io/metadata.name": {}
                }
              }
            }
          }
        ]
      },
      "spec": {
        "finalizers": [
          "kubernetes"
        ]
      },
      "status": {
        "phase": "Active"
      }
    },
    {
      "metadata": {
        "name": "kube-system",
        "uid": "a1f37f94-aae9-4dc4-8896-8285d3c533b7",
        "resourceVersion": "8",
        "creationTimestamp": "2024-03-09T09:59:41Z",
        "labels": {
          "kubernetes.io/metadata.name": "kube-system"
        },
        "managedFields": [
          {
            "manager": "kube-apiserver",
            "operation": "Update",
            "apiVersion": "v1",
            "time": "2024-03-09T09:59:41Z",
            "fieldsType": "FieldsV1",
            "fieldsV1": {
              "f:metadata": {
                "f:labels": {
                  ".": {},
                  "f:kubernetes.io/metadata.name": {}
                }
              }
            }
          }
        ]
      },
      "spec": {
        "finalizers": [
          "kubernetes"
        ]
      },
      "status": {
        "phase": "Active"
      }
    },
    {
      "metadata": {
        "name": "kubernetes-dashboard",
        "uid": "b953157f-2e8a-4c9d-9b13-fdd3b4b89882",
        "resourceVersion": "817",
        "creationTimestamp": "2024-03-09T10:09:28Z",
        "labels": {
          "addonmanager.kubernetes.io/mode": "Reconcile",
          "kubernetes.io/metadata.name": "kubernetes-dashboard",
          "kubernetes.io/minikube-addons": "dashboard"
        },
        "annotations": {
          "kubectl.kubernetes.io/last-applied-configuration": "{\"apiVersion\":\"v1\",\"kind\":\"Namespace\",\"metadata\":{\"annotations\":{},\"labels\":{\"addonmanager.kubernetes.io/mode\":\"Reconcile\",\"kubernetes.io/minikube-addons\":\"dashboard\"},\"name\":\"kubernetes-dashboard\"}}\n"
        },
        "managedFields": [
          {
            "manager": "kubectl-client-side-apply",
            "operation": "Update",
            "apiVersion": "v1",
            "time": "2024-03-09T10:09:28Z",
            "fieldsType": "FieldsV1",
            "fieldsV1": {
              "f:metadata": {
                "f:annotations": {
                  ".": {},
                  "f:kubectl.kubernetes.io/last-applied-configuration": {}
                },
                "f:labels": {
                  ".": {},
                  "f:addonmanager.kubernetes.io/mode": {},
                  "f:kubernetes.io/metadata.name": {},
                  "f:kubernetes.io/minikube-addons": {}
                }
              }
            }
          }
        ]
      },
      "spec": {
        "finalizers": [
          "kubernetes"
        ]
      },
      "status": {
        "phase": "Active"
      }
    }
  ]
```

## Some links

[kubernetes-api](https://iximiuz.com/en/posts/kubernetes-api-call-simple-http-client/): How To Call Kubernetes API using Simple HTTP Client.



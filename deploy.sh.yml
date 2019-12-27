docker build -t mohgamalmoh/multi-client:latest -t mohgamalmoh/multi-client:$SHA -f ./client/Dockerfile ./client
docker build -t mohgamalmoh/multi-server:latest -t mohgamalmoh/multi-server:$SHA -f ./server/Dockerfile ./server
docker build -t mohgamalmoh/multi-worker:latest -t mohgamalmoh/multi-worker:$SHA -f ./worker/Dockerfile ./worker

docker push mohgamalmoh/multi-client:latest
docker push mohgamalmoh/multi-server:latest
docker push mohgamalmoh/multi-worker:latest

docker push mohgamalmoh/multi-client:$SHA
docker push mohgamalmoh/multi-server:$SHA
docker push mohgamalmoh/multi-worker:$SHA

kubectl apply -f k8s
kubectl set image deployments/server-deployment server=mohgamalmoh/multi-server:$SHA
kubectl set image deployments/client-deployment client=mohgamalmoh/multi-client:$SHA
kubectl set image deployments/worker-deployment worker=mohgamalmoh/multi-worker:$SHA

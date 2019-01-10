# kafkainstall

#To track install steps for AMQ streams

 oc login https://master.<blah>.openshiftworkshop.com:443 --token=blah
 
 
 oc new-project myproject

cd ~/wherever your install zip is>


oc apply -f ./install_and_examples/install/cluster-operator -n myproject


oc apply -f ./install_and_examples/examples/templates/cluster-operator/ -n myproject


oc apply -f ./install_and_examples/examples/kafka/kafka-ephemeral.yaml 


oc apply -f install_and_examples/examples/kafka-connect/kafka-connect.yaml 


oc run kafka-producer -ti --image=registry.access.redhat.com/amqstreams-1/amqstreams10-kafka-openshift:1.0.0 --rm=true --restart=Never -- bin/kafka-console-producer.sh --broker-list my-cluster-kafka-bootstrap:9092 --topic my-topic


oc run kafka-consumer -ti --image=registry.access.redhat.com/amqstreams-1/amqstreams10-kafka-openshift:1.0.0 --rm=true --restart=Never -- bin/kafka-console-consumer.sh --bootstrap-server my-cluster-kafka-bootstrap:9092 --topic my-topic --from-beginning
  
  #all done adding

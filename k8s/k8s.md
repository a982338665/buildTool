
### �ٷ��ĵ���https://www.kubernetes.org.cn/doc-11
### �ٷ��ĵ���http://docs.kubernetes.org.cn/227.html

**1.k8s��װ��**
    
    1.��װdocker
    2.docker��װ���֮��ʼ��װ kubeadm��kubelet��kubectl������������ڹٷ��ṩ�Ĺȸ辵�������޷����ʣ�����ʹ�ð����ƾ���ֿ����������
      ���yumԴ����:
      cat <<EOF > /etc/yum.repos.d/kubernetes.repo
      [kubernetes]
      name=Kubernetes
      baseurl=http://mirrors.aliyun.com/kubernetes/yum/repos/kubernetes-el7-x86_64
      enabled=1
      gpgcheck=0
      repo_gpgcheck=0
      gpgkey=http://mirrors.aliyun.com/kubernetes/yum/doc/yum-key.gpg http://mirrors.aliyun.com/kubernetes/yum/doc/rpm-package-key.gpg
      EOF
    3.yumԴ������ɣ���ʼ��װkubelet��kubeadm��kubectl������ͼ��complete��ʾ��װ���
      yum -y install kubelet kubeadm kubectl
    4.

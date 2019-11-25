<a name="4942">

# [SUB]Core Concepts

<div><span>

<div>

<div><span style="font-size: 16pt; font-weight: bold;">Core Concepts</span></div>

<div><span style="font-size: 12pt; font-weight: bold;">Entry</span></div>

<div>entry point�� internal dependency graph�� ������ �����ϱ� ���� � ��� ������ ����ؾ� �ϴ��� ��Ÿ����. ������ entry point�� � �ٸ� ���� ���̺귯���� �����ϴ����� �ľ��Ѵ�.(������������)</div>

<div>�⺻ entry point ���� <span style="background-color: rgb(255, 250, 165);-evernote-highlight:true;">./src/index.js</span> ������ �Ʒ��� ���� �ٸ� ��� (or multiple entry points)�� ������ �� �ִ�.</div>

<div>![]([SUB]Core Concepts_files/Image.png)</div>

<div><span style="font-size: 12pt; font-weight: bold;">Output</span></div>

<div>output ������Ƽ�� ������ ��� bundles�� ��������, � name���� ������ ���� ���� ���̴�. �⺻���� �� ��� ������ <span style="background-color: rgb(255, 250, 165);-evernote-highlight:true;">./dist/main.js</span> �̰� �ٸ� ���ϵ��� ��� <span style="background-color: rgb(255, 250, 165);-evernote-highlight:true;">./dist</span> ������ �����Ǿ� �ִ�.</div>

<div>![]([SUB]Core Concepts_files/Image [1].png)</div>

<div>���� ������ output.path�� output.filename���� ����� �����Ѵ�. �ڵ��� ���� �ִ� path�� ���� ��θ� �����ϴ� �� ���Ǵ� core node.js ����̴�.</div>

<div>[output �Ӽ��� �� ���� ������ �� �� ������ �ڼ��� ���� �ش� section�� ����.]</div>

<div><span style="font-weight: bold; font-size: 12pt;">Loaders</span></div>

*   <div>ES5 <> ES6,? react�� JSX, SASS���� ��ȯ�� ����.</div>

<div>������ ������ JS�� JSON ���ϸ��� �����մϴ�. �δ��� ������ �ٸ� type�� ������ ó���ϰ� ����� application���� �Һ�Ǵ� valid�� ���� ��ȯ�� �� �ֵ��� �Ͽ� dependency graph�� �߰��� �� �ֵ��� �Ѵ�.</div>

<div>���� ���ؿ��� �δ��� webpack config���� �� ���� ������Ƽ�� ������ �ֽ��ϴ�.</div>

<div>![]([SUB]Core Concepts_files/Image [2].png)</div>

<div>���� �������� ���� ��⿡ ���� �� ����(test,use) rules �Ӽ��� ������ �ִ�. �̰��� ���� �����Ϸ����� ������ �͵��� �˷��ش�.</div>

<div>*.txt���� �� require() �Ǵ� import ���� ������ bundles�� �߰��ϱ� ���� raw-loader�� ����Ͽ� ��ȯ�϶�. ��� ����� ������ ���̴�.</div>

<div><font style="font-size: 12pt;"><span style="font-size: 12pt; font-weight: bold;">Plugins</span></font></div>

<div>�δ��� Ư���� ������ ����� ��ȯ�ϱ� ���Ͽ� ���Ǵ� �ݸ�, plugins�� bundle ����ȭ, asset management, ȯ�� ���� ���԰� ���� �������� �۾��� ������ �� �ִ�.</div>

<div>plugins���� ����ϱ� ���ؼ��� require()�� ����Ͽ� plugin array�� �߰��ؾ��Ѵ�. config���� �÷������� ������ ����� �� �ְ� new �����ڿ� �Բ� ȣ���Ͽ� �ν��Ͻ��� �����ؾ� �Ѵ�.</div>

<div>![]([SUB]Core Concepts_files/Image [3].png)</div>

<div>���� ������ html-webpack-plugin�� ������ ��� bundles�� �ڵ������� HTML���Ͽ� �����Ͽ� �����ϴ� ���̴�.</div>

<div><span style="font-weight: bold; font-size: 12pt;">Mode</span></div>

<div>mode parameter�� development, production, none���� �����ϸ� �� ȯ�濡 �ش��ϴ� ����ȭ�� ������ �� �ִ�. �⺻���� <span style="background-color: rgb(255, 250, 165);-evernote-highlight:true;">production</span></div>

<div>![]([SUB]Core Concepts_files/Image [4].png)</div>

<div>[���� �ľ��ϱ�δ�...? development�� bundles.js�ҽ����� �� �̻ڰ� ������ production�� ����ȭ,minify�ؼ� ����]</div>

<div><span style="font-weight: bold; font-size: 12pt;">Browser Compatibility</span></div>

<div>������ ES5�� �ؼ��ϴ� ��� ������(IE8 and below ����)�� ���� ������ �Ѵ�. ������ import() �� require.ensure()�� ���Ͽ� promise�� �ʿ��ϱ� �����̴�. ���� ���� ������ ���� ������ ������ �ʿ��ϸ� load a polyfill�� ����ض�.(Ȩ������ ����)</div>

</div>

</span></div>

</a>
<template>
    <div class="sidebar">
        <el-menu :default-active="onRoutes" class="el-menu-vertical-demo" theme="dark" unique-opened router>
            <template v-for="item in items">
                <template v-if="item.subs">
                    <el-submenu :index="item.index">
                        <!--<template slot="title"><i :class="item.icon"></i>{{ item.title }}</template>-->
                        <template slot="title">
                            <icon :name="item.icon"></icon>
                            <span> {{ item.title }}</span></template>
                        <el-menu-item v-for="(subItem,i) in item.subs" :key="i" :index="subItem.index">{{ subItem.title
                            }}
                        </el-menu-item>
                    </el-submenu>
                </template>
                <template v-else>
                    <el-menu-item :index="item.index">
                        <icon :name="item.icon"></icon>
                        <span>{{ item.title }}</span>
                    </el-menu-item>
                </template>
            </template>
        </el-menu>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                items: [
                    {
                        icon: 'dashboard',
                        index: 'dashboard',
                        title: '仪表盘'
                    },
                    {
                        icon: 'server',
                        index: '2',
                        title: '主机监控',
                        subs: [
                            {
                                index: 'groups',
                                title: '主机组'
                            },
                            {
                                index: 'hosts',
                                title: '主机'
                            },
                            {
                                index: 'waterfall',
                                title: '主机瀑布'
                            }
                        ]
                    },
                    {
                        icon: 'bell',
                        index: 'events',
                        title: '告警事件'
                    },
                    {
                        icon: 'heartbeat',
                        index: '4',
                        title: '应用监控',
                        subs: [
                            {
                                index: 'apache',
                                title: 'Apache 监控'
                            },
                            {
                                index: 'ftp',
                                title: 'FTP 监控'
                            },
                            /*{
                                index: 'groups',
                                title: 'Tomcat 监控'
                            },
                            {
                                index: 'hosts',
                                title: 'Nginx 监控'
                            },
                            {
                                index: 'waterfall',
                                title: 'Node 监控'
                            }*/
                        ]
                    },
                    {
                        icon: 'database',
                        index: '5',
                        title: '存储监控',
                       /* subs: [
                            {
                                index: 'groups',
                                title: 'MySQL 监控'
                            },
                            {
                                index: 'hosts',
                                title: 'Oracle 监控'
                            },
                            {
                                index: 'waterfall',
                                title: 'Redis 监控'
                            }
                        ]*/
                    },
                ]
            }
        },
        computed: {
            onRoutes() {
                return this.$route.path.replace('/', '');
            }
        }
    }
</script>

<style scoped>
    .sidebar .el-menu-item * {
        vertical-align: middle;
    }

    .sidebar .el-submenu * {
        vertical-align: middle;
    }

    .sidebar {
        display: block;
        position: absolute;
        width: 250px;
        left: 0;
        top: 70px;
        bottom: 0;
        background: #2E363F;
    }

    .sidebar > ul {
        height: 100%;
    }

    * {
        margin: 0;
        padding: 0;
    }

</style>
